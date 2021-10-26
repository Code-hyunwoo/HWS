# :boom: Workshop

---



​																					

### Model

```python
class Artist(models.Model):
    name = models.CharField(max_length=200)
    
class Music(models.Model):
    artist = models.ForeignKey(Artist, on_delete=models.CASCADE, related_name='musics')
    title = models.CharField(max_length=200)
```

​																																												

### Serializer.py

```python
from rest_framework import serializers
from .models import Artist,Music

class ArtistListSerializer(serializers.ModelSerializer):

    class Meta:
        model = Artist
        fields = ('id','name',)

class MusicSerializer(serializers.ModelSerializer):

    class Meta:
        model = Music
        fields = ('id','title','artist',)
        read_only_fields=('artist',)

class ArtistSerializer(serializers.ModelSerializer):
    music_set = MusicSerializer(many=True, read_only=True)
    music_count = serializers.IntegerField(source='music_set.count',read_only=True)
    class Meta:
        model = Artist
        fields = ('id','name','music_set','music_count',)

class MusicListSerializer(serializers.ModelSerializer):

    class Meta:
        model = Music
        fields = ('id','title',)
```

​																																											

​																																							

### views.py

```python
from django.shortcuts import render

# Create your views here.
from django.shortcuts import get_object_or_404
from .models import Artist,Music
from .serializers import (
    ArtistListSerializer,
    ArtistSerializer,
    MusicListSerializer,
    MusicSerializer
)
from rest_framework import status
from rest_framework.decorators import api_view
from rest_framework.response import Response



@api_view(['GET','POST'])
def artist_list(request):
    if request.method =='GET':
        artists = get_list_or_404(Artist)
        serializer = ArtistListSerializer(artists,many=True) 
        return Response(data=serializer.data)
    
    elif request.method =='POST':
        serializer = ArtistListSerializer(data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
        return Response(data=serializer.data, status=status.HTTP_201_CREATED)
    
@api_view(['GET','POST'])
def artist_detail(request, artist_pk):
    artist = get_object_or_404(Artist, pk=artist_pk)
    if request.method == 'GET':
        serializer = ArtistSerializer(artist)
        return Response(serializer.data)

@api_view(['POST'])  
def music_create(request, artist_pk):
    artist = get_object_or_404(Artist, pk=artist_pk)
    serializer = MusicSerializer(data=request.data)
    if serializer.is_valid(raise_exception=True):
        serializer.save(artist=artist)
        return Response(serializer.data, status=status.HTTP_201_CREATED)
    
@api_view(['GET'])
def music_list(request):
    musics = get_list_or_404(Music)
    serializer = MusicSerializer(musics, many=True)
    return Response(serializer.data)

    
@api_view(['GET', 'DELETE', 'PUT'])   
def music_detail(request, music_pk):
    music = get_list_or_404(Music, pk=music_pk)
    if request.method == 'GET':
        serializer = MusicSerializer(music)
        return Response(serializer.data)

    elif request.method == 'DELETE':
        music.delete()
        data = {
            'delete': f'댓글 {music_pk}번이 삭제되었습니다.'
        }
        return Response(data, status=status.HTTP_204_NO_CONTENT)

    elif request.method == 'PUT':
        serializer = MusicSerializer(instance=music, data=request.data)
        if serializer.is_valid(raise_exception=True):
            serializer.save()
            return Response(serializer.data)
```

