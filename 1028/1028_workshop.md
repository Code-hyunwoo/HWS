# :boom: Workshop

---



### Todo app



```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .done {
            text-decoration: line-through;
        }


    </style>
</head>
<body>
    <form action="#">
        <input type="text">
        <button>Todo</button>
    </form>
    <ul>

    </ul>

    <script>

        const form = document.querySelector('form')

        function addTodo (event) {
            event.preventDefault()

            const input = document.querySelector('input')
            const content = input.value
            if (content.trim()) {

                const li = document.createElement('li')
                li.innerText = content
        
                const ul = document.querySelector('ul')
                ul.appendChild(li)

                const deletebtn = document.createElement('button')
                deletebtn.innerText = 'X'

                li.appendChild(deletebtn)

                deletebtn.addEventListener('click', function(){
                    li.remove()
                })

                li.addEventListener('click', function(event){
                    // if (event.target.classList.length){
                    //     event.target.classList.remove('done')
                    //     console.log(event)
                    // } else {
                    //     event.target.classList.add('done')
                    //     console.log(event)
                    // }
                    if (event.target.classList.contains('done')) {
                        event.target.classList.remove('done')
                    } else {
                        event.target.classList.add('done')
                    }
                })
            } else {
                alert('할 일을 입력해주세요.')
            }

            event.target.reset()
        }

        form.addEventListener('submit', addTodo)
 

    </script>
</body>
</html>
```

