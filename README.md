

## What did you find hardest, 

I spent a lot of time in searching and studying the js functions used to make the collapsable work, and the click event. Now it looks ridiculously simple, this started when I started debugging in "inspect" mode on the browser. And the MDN or w3 finally started making sense. 



## What did you look up,

During the challenge I saved some of the pages that helped in here:

https://liferay.atlassian.net/wiki/spaces/~712020753153f21ae44f0da3375d9e496f9ef7/pages/5499781136/Frontend+Challange




## What would you do differently with more time.


With more time I would try to search for a way to complete the challenge's requirements that I couldn't finish. On that note, the accessibility keyboard features looked the most interesting and I wanted to search how it works. Other than the SCSS requirements, the layout or the event listener I have the impression that I would find it easily in either w3 or MDN and try to understand to make it work. Moreover I would have definitely not spended so much time trying to solve a bug in the Collapsable, I think the time spent on it was too much. Maybe I should have focused my time on trying “easier” requirements.










## Script Code "progression"
### JS First try:


```js

    var coll = document.getElementsByClassName("collapsible");
    var i;

    for (i = 0; i < coll.length; i++) {
    coll[i].addEventListener("click", function() {
        this.classList.toggle("active");
        var content = this.nextElementSibling;

        if (content.style.display === "block") {
        content.style.display = "none";
        } else {
        content.style.display = "block";
        }

    });
    }

```


### JS Second try:

```js


    for (i = 0; i < coll.length; i++) {
        coll[i].addEventListener("click", function() {
            
            this.classList.toggle("active");

            const aux = i;

            if (this.classList.toggle("active")){
                for(j = 0; j < coll.length; j++){
                    coll[j].nextElementSibling.style.display = "none";
                }
                // coll[aux].nextElementSibling.style.display = "block";
            }
            coll[aux].nextElementSibling.style.display = "block";

        });
    }


```


### JS third try:


```js

    for (i = 0; i < coll.length; i++) {
        coll[i].addEventListener("click", function() {
            
            const aux = i;

            for(j = 0; j < coll.length; j++){
                coll[j].nextElementSibling.style.display = "none";
            }

            // tudo em funcao do button i clicado no momento
            if(this.nextElementSibling.style.display === "block"){
                this.nextElementSibling.style.display = "none";
            }else{
                this.nextElementSibling.style.display = "block";
            }

        });
    }


```


### JS fourth try

The last thing IU was trying to do was "close a chosen question". After debugging I understood why closing it does not work. But I could not find a solution, yet.

```js


    var coll = document.getElementsByClassName("collapsible");
    var i;
    const flagOpen = false;

    for (i = 0; i < coll.length; i++) {
        coll[i].addEventListener("click", function() {
            
            const aux = i;
            

            for(j = 0; j < coll.length; j++){
                coll[j].nextElementSibling.style.display = "none";
            }

            if((this.nextElementSibling.style.display === "block") || flagOpen === true){
                this.nextElementSibling.style.display = "none";
                flagOpen = false;
            }else {
                this.nextElementSibling.style.display = "block";
                flagOpen = true;
            }

        });
    }

```


