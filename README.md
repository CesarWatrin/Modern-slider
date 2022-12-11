# modern-vue3-slider

Example : https://dribbble.com/shots/11431212-Carousel-experimentation <br>
Video (mp4) : https://cdn.dribbble.com/users/27981/screenshots/11431212/media/976bf26b62d07e68c9111c1dacee7c26.mp4

Test algo :  

0   800 150 0
1   400 800 150 0
2   200 400 800 150 0
3   200 200 400 800 150 0
4   200 200 200 400 800 150 0

b = 800 150 0
r = null
for (i in n)
    r = b
    if i >= 1
        r = (200 * (i - 1)) + 400 + b
