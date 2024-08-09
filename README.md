# project1
[09:31, 8/9/2024] Pushpa: <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Animated Image Slider</title>

    <link rel="stylesheet" href="style.css">

</head>
<body>
    
    <header>

        <nav>
            <a href="" class="active">Home</a>
            <a href="">About</a>
            <a href="">Portfolio</a>
            <a href="">Services</a>
            <a href="">Contact</a>
        </nav>

    </header>


    <div class="carousel">

        <div class="list">

            <div class="item" style="background-image: url(image/eagel1.jpg);">
                <div class="content">
                    <div class="title">SLIDER</div>
                    <div class="name">EAGLE<…
[09:31, 8/9/2024] Pushpa: @import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,100;0,200;0,300;0,400;0,500;0,600;0,700;0,800;0,900;1,100;1,200;1,300;1,400;1,500;1,600;1,700;1,800;1,900&display=swap');

*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: 'Poppins', sans-serif;
}

/* Header section */

header{
    width: 100%; 
    max-width: 100%;
    padding-left: 100px;
    height: 50px;
    display: flex;
    align-items: center;
    position: relative;
    z-index: 1000;
}

header nav a{
    color: #fff;
    margin-right: 5px;
    padding: 5px 10px;
    font-size: 16px;
    transition: 0.2s;
    text-decoration: none;
}

a.active{
    background: #14ff72cb;
    border-radius: 2px;
}

a:hover{
    background: #14ff72cb;
    border-rad…
[09:31, 8/9/2024] Pushpa: var nextBtn = document.querySelector('.next'),
    prevBtn = document.querySelector('.prev'),
    carousel = document.querySelector('.carousel'),
    list = document.querySelector('.list'), 
    item = document.querySelectorAll('.item'),
    runningTime = document.querySelector('.carousel .timeRunning') 

let timeRunning = 3000 
let timeAutoNext = 7000

nextBtn.onclick = function(){
    showSlider('next')
}

prevBtn.onclick = function(){
    showSlider('prev')
}

let runTimeOut 

let runNextAuto = setTimeout(() => {
    nextBtn.click()
}, timeAutoNext)


function resetTimeAnimation() {
    runningTime.style.animation = 'none'
    runningTime.offsetHeight /* trigger reflow */
    runningTime.style.animation = null 
    runningTime.style.animation = 'runningTime 7s linear 1 forwards'
}


function showSlider(type) {
    let sliderItemsDom = list.querySelectorAll('.carousel .list .item')
    if(type === 'next'){
        list.appendChild(sliderItemsDom[0])
        carousel.classList.add('next')
    } else{
        list.prepend(sliderItemsDom[sliderItemsDom.length - 1])
        carousel.classList.add('prev')
    }

    clearTimeout(runTimeOut)

    runTimeOut = setTimeout( () => {
        carousel.classList.remove('next')
        carousel.classList.remove('prev')
    }, timeRunning)


    clearTimeout(runNextAuto)
    runNextAuto = setTimeout(() => {
        nextBtn.click()
    }, timeAutoNext)

    resetTimeAnimation() // Reset the running time animation
}

// Start the initial animation 
resetTimeAnimation()
