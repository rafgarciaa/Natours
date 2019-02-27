## [Natours](https://rafgarciaa.github.io/Natours/)
A small landing page for a travel agency startup. This coding exercise capitalizes on the capabilities of HTML and CSS.

## Goals
1) Be up to speed with the most modern and advanced CSS properties and techniques;

2) Be ready to build responsive layouts for all kind of devices and situations;

3) Truly understand how CSS works behind the scenes;

4) Be able to architect large CSS codebases for reusability and maintainability using Sass.

## Features & Code Snippets
These are some of the key features of this landing page. It's amazing how we can capitalize the different tricks and techniques available in CSS.

```@keyframes``` animations
Allows for element to transition from one position to another. This is achieved by defining where elements are positioned at the beginning and at the end of the animation (defined as 0% - 100%  - see below).

![@keyframes animations](https://gfycat.com/ElatedYawningDrongo)
```css
@keyframes moveInLeft {
    /* Before the animation starts */
    0% {
        opacity: 0;
        transform: translateX(-10rem);
    }

    /* 60% {
        transform: rotate(180deg);
    } */

    80% {
        transform: translateX(1rem);
    }

    /* When the animation ends */
    100% {
        opacity: 1;
        transform: translate(0);
    }
}

@keyframes moveInRight {
    /* Before the animation starts */
    0% {
        opacity: 0;
        transform: translateX(10rem);
    }

    80% {
        transform: translateX(-1rem);
    }

    /* When the animation ends */
    100% {
        opacity: 1;
        transform: translate(0);
    }
}

@keyframes moveInBottom {
    /* Before the animation starts */
    0% {
        opacity: 0;
        transform: translateY(3rem);
    }
    
    /* When the animation ends */
    100% {
        opacity: 1;
        transform: translateX(0);
    }
}
```

Image Transitions - each image is emphasized as it's hovered over giving a 3d-esque feel to the webpage. This is achieved by scaling-up the current image being hovered over and scale-down the other photos.

![Image Transitions](https://gfycat.com/SoulfulAdvancedAtlasmoth)
```css
.composition {
    position: relative;

    // photo styling
    &__photo {
        width: 55%;
        box-shadow: 0 1.5rem 4rem rgba($color-black, .4);
        border-radius: 2px;
        position: absolute;
        z-index: 10;
        transition: all .2s;
        outline-offset: 2rem;

        // photo positions
        &--p1 {
            left: 0;
            top: -2rem;
        }

        &--p2 {
            right: 0;
            top: 3rem;
        }

        &--p3 {
            left: 20%;
            top: 12rem;
        }

        // hover effect on all photos
        &:hover {
            outline: 1.5rem solid $color-primary;
            transform: scale(1.05) translateY(-.5rem);
            box-shadow: 0 2.5rem 4rem rgba($color-black, .5);
            z-index: 100;
        }
    }

    // composition:hover composition__photo:not(:hover)
    // all the photos except the photo currently hovered will scale smaller
    &:hover &__photo:not(:hover) {
        transform: scale(.95);
    }
}
```

Card Animations - my most favorite feature of this page. This card animation is achieved by creating two div elements on top of each other and declaring the property of both the `front` and the `back` side of each card ```backface-visibility: hidden``` and then giving each side it's own styling accordingly. This segment of this page also reuses the button component similar to the "Discover our tours" button at the top of the page.

![card animations](https://gfycat.com/TemptingPeskyLadybird)
```css
&__side {
    height: 52rem;
    transition: all .8s ease;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    backface-visibility: hidden;
    border-radius: 3px;
    overflow: hidden; // this is written bc the image overflows on top of the parent element which is the card (therefore remove the border radius)
    box-shadow: 0 1.5rem 4rem rgba($color-black, .15);
    
    &--front {
        background-color: $color-white;
    }
    
    &--back {
        transform: rotateY(180deg);

        &-1 {
            background-image: linear-gradient(to right bottom, $color-secondary-light, $color-secondary-dark);
        }

        &-2 {
            background-image: linear-gradient(to right bottom, $color-primary-light, $color-primary-dark);
        }

        &-3 {
            background-image: linear-gradient(to right bottom, $color-tertiary-light, $color-tertiary-dark);
        }
    }
}

&:hover &__side--front {
    transform: rotateY(-180deg);
}

&:hover &__side--back {
    transform: rotateY(0);
}
```

### Technologies & Tools
+ HTML5
+ CSS3
+ npm
+ live-server
+ node-sass