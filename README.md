# NTUOSS-BootstrapWorkshop

*by Suyash Lakhotia for NTU Open Source Society*

This workshop is based on Bootstrap v3.3.5 and assumes basic knowledge of HTML & CSS.

***Disclaimer*** *-* *This document is only meant to serve as a reference for the attendees of the workshop. It does not cover all the concepts or implementation details discussed during the actual workshop.*

###Workshop Details:<br>
**When?**: Friday, 18 Sep 2015. 6:30 PM - 8:30 PM.<br>
**Where?**: Theatre@TheNest, Innovation Centre, Nanyang Technological University<br>
**Who?**: NTU Open Source Society<br>

###Questions?
Raise your hand at any time during the workshop or shoot me an [e-mail](mailto:suyashlakhotia@gmail.com) later.

###Errors?
If you find any mistake (typo or anything else), please make a pull request or [post an issue](https://github.com/SuyashLakhotia/NTUOSS-BootstrapWorkshop/issues/new)! Thanks!<br><br>


## Task 0 - Initial Setup
1. Download a text editor if you don't have one already. I would recommend either:
  1. [Sublime Text 2](http://www.sublimetext.com/2)
  2. [Brackets](http://brackets.io)
2. Download Boostrap [here](https://github.com/twbs/bootstrap/releases/download/v3.3.5/bootstrap-3.3.5-dist.zip).
3. Download [this project](https://github.com/SuyashLakhotia/NTUOSS-BootstrapWorkshop/archive/master.zip) to get started.


## Task 1 - Setting Up Bootstrap
1. Unzip the Bootstrap distribution and copy all the contents into the 'BootstrapWorkshop' folder.
2. Open up *index.html* in your preferred text editor.
3. Open up *index.html* in your browser as well or use *Live Preview* if you're using Brackets.
4. Replace the current `<head>` tag in *index.html* with the following code:

```html
<head>
	<meta name="viewport" content="width=device-width, initial-scale=1">

    <link rel="stylesheet" href="css/bootstrap.min.css">
    <link rel="stylesheet" href="custom.css">
    
    <script src="http://code.jquery.com/jquery-1.10.2.min.js"></script>
    <script src="js/bootstrap.min.js"></script>

    <title>NTUOSS Bootstrap Workshop</title>
</head>
```

The above code allows your HTML file to be linked to your custom CSS stylesheet, Bootstrap's CSS & JavaScript as well as JQuery.

**Note:** It is important to link your own CSS stylesheet after Bootstrap's if you wish to override any of the default classes.


## Task 2 - Creating a Jumbotron
See the code for the title of the page in *index.html*? It should look something like this:

```html
<h1>HELLO, WORLD!</h1>
<h3>This might be my first <em>Bootstrapped</em> website.</h3>
```

This looks pretty simple. Let's add some style to it by converting it into something Bootstrap calls a *Jumbotron*.

1. Wrap the code inside a `<div>`. This is good programming practice and makes implementing CSS classes a lot easier.
2. Let's assign the default `.jumbotron` class to the div. Just like that, Bootstrap allows you to make a pretty appealing title for your page.
3. Try adding a `.container` class before the `.jumbotron` class. Did you notice what changed?

```html
<div class="container jumbotron">
	<h1>HELLO, WORLD!</h1>
	<h3>This might be my first <em>Bootstrapped</em> website.</h3>
</div>
```


## Task 3 - Containers
Bootstrap requires a containing element to wrap site contents and house the grid system. However, nesting these containers is highly discouraged. You may choose one of two containers to use in your projects:

`.container` is a responsive fixed size container.

```html
<div class="container">
	...
</div>
```

`.container-fluid` is a full-width container that spans the entire width of the viewport.

```html
<div class="container-fluid">
	...
</div>
```

Try implementing both these classes in the jumbotron you made in **Task 1** and see how it changes. You will notice that by default, the jumbotron imitates the `.container-fluid` class.


## Task 4 - The Grid System
Now that we're done with the title of the page, let's move on to the bundle of text right below the title. It looks pretty messy, doesn't it? Let's fix that.

Bootstrap offers a simple grid system made up of rows & columns where each row has exactly 12 columns. This allows you to layout any HTML element fairly easily. Let's try doing that for the three paragraphs of text.

1. Wrap each paragraph inside the `#text_row` div with a `<div>`.
2. In order to 'activate' the grid system, we have to create a row. In the overarching `<div>` i.e. `#text_row`, add the `.container-fluid` & `.row` classes. This creates a row with everything inside the `<div>` (i.e. the three paragraphs). Things still pretty much look the same right?
3. Let's assign columns to each paragraph now. Add the `.col-md-4` class to each paragraph in their own `<div>` tags. This assigns 4 columns to each of the paragraphs.

```html
<div class="container-fluid row" id="text_row">
        <div class="col-md-4">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
        <div class="col-md-4">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
        <div class="col-md-4">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
    </div>
```

What we have just done is assign 1/3 of the viewport to each paragraph by putting each paragraph in 4 columns out of a total of 12 columns. Feel free to play around with these numbers but remember that the total number of columns in a row must not exceed 12.

Now, let's say we wanted the first paragraph to start after one column of space. In that case, we would use the `.col-md-offset-X` class where `X` represents the number of columns to offset by.

```html
<div class="container-fluid row" id="text_row">
        <div class="col-md-3 col-md-offset-1">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
        <div class="col-md-4">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
        <div class="col-md-4">
            <p>Lorem ipsum dolor sit amet...</p>
        </div>
    </div>
```

**Note:** When an offset column is added, it is important to decrease the actual content's width by the offset column's width so that the total number of columns in the row is still 12.

Read more about Bootstrap's grid system [here](http://getbootstrap.com/css/#grid).


## Break - Parallax Scrolling
Let's take a quick break from Bootstrap for a bit.

'Parallax Scrolling' is a cool CSS trick that you may have encountered in many websites such as [this one](http://callmenick.com/_development/simple-parallax-effect/). It allows the background to stay fixed when the user is scrolling. So, how is this done?

It's actually pretty simple. All you need to do is add one simple line of CSS to your `<div>`:

```css
background-attachment: fixed;
```

Inside the project files, this is what your CSS for the `#img_text` div should look like after adding the above line:

```css
#img_text {
    color: white;
    text-align: center;
    background-image: url(img/bg_img.jpg);
    background-attachment: fixed;		/* Parallax Scrolling Effect */
    margin: 20px 0px 20px 0px;
    height: 300px;
}

```

## Task 5 - Images
Alright, let's get back to it. Let's try arranging all the images below the parallax scrolling we just built. Try implementing the grid system from **Task 4** in order to give each of the images equal width in a row. Your finished code should look a little something like this:

```html
<div class="row" id="img_row">
	<div class="col-md-4">
		<img src="http://lorempixel.com/600/600/cats/1">
	</div>
        
	<div class="col-md-4">
   		<img src="http://lorempixel.com/600/600/cats/2">
   	</div>
        
   	<div class="col-md-4">
 		<img src="http://lorempixel.com/600/600/cats/3">
	</div>
</div>
```

You must have noticed that due to the images being wider than the columns, they get cropped. Let's fix that. Add the `.img-responsive` class to each `<img>` tag and let the magic happen. Just like that, Bootstrap automatically fits the images according to the width assigned to it. This also helps when viewing the website through a mobile browser. Try resizing your browser. The images should shrink automatically.

```html
<div class="row" id="img_row">
	<div class="col-md-4">
		<img src="http://lorempixel.com/600/600/cats/1" class="img-responsive">
	</div>
        
	<div class="col-md-4">
   		<img src="http://lorempixel.com/600/600/cats/2" class="img-responsive">
   	</div>
        
   	<div class="col-md-4">
 		<img src="http://lorempixel.com/600/600/cats/3" class="img-responsive">
	</div>
</div>
```

In addition to the `.img-responsive` class, Bootstrap also offers the following classes for images:

1. `.img-rounded`: Adds rounded corners to the image.
2. `.img-circle`: Crops the image into a circle.
3. `.img-thumbnail`: Adds a thumbnail-esque border to the image.


## Task 6 - Buttons
Look at the "Back To Top" link at the bottom of the page. That is something that is clearly built for function and not form. Let's give it a more button-y feel.

Bootstrap comes with various button styles that can be implemented extremely easily onto any standalone link.

1. Locate the link inside the `#button_div` div.
2. Wrap the text inside the `<a>` tags with `<button>` tags.
3. Add a `type` attribute to the `<button>` tag and set it to `"button"`.
4. Next, add two classes to the `<button>` tag: `.btn` & `.btn-primary`.

Here's how it's implemented in code:

```html
<a href="#">
	<button type="button" class="btn btn-primary">Back to Top</button>
</a>
```

As you can see, the once odd-looking link now looks like an appealing button. However, Bootstrap does not only offer one type of button. Below is a list of the different button classes Bootsrap offers. Feel free to play around with them:

1. `.btn-default`
2. `.btn-success`
3. `.btn-primary`
4. `.btn-info`
5. `.btn-warning`
6. `.btn-danger`
7. `.btn-link`


## Task 7 - Navbar
A navbar is a great way to get around websites or even around a particular webpage. Bootstrap offers a fairly simple way to implement a navbar.

Since implementing a navbar in this project involves entirely new lines of code, copy the following lines of code into *index.html* right above the jumbotron first.

```html
<nav class="navbar navbar-default">
    <div class="container-fluid">
        <div class="navbar-header">
            <button type="button" class="navbar-toggle collapsed" data-toggle="collapse" data-target="#example-navbar" aria-expanded="false">
                <span class="sr-only">Toggle Navigation</span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
                <span class="icon-bar"></span>
            </button>
            <a class="navbar-brand" href="#">NTUOSS</a>
        </div>

        <div class="collapse navbar-collapse" id="example-navbar">
            <ul class="nav navbar-nav">
                <li><a href="#text_row">Text Row</a></li>
                <li><a href="#img_row">Image Row</a></li>
            </ul>
        </div>
    </div>
</nav>
```

Look at the navbar on your browser and try to compare the different parts to the code. As can be seen, the *brand* of the website appears on the extreme left of the navbar and all the other links specified in the `<ul>` appear to the right of that brand.

**Note**: To create a link to a part of the same webpage, the `href` attribute of the link should point to the `id` attribute of the destination HTML element.

This navbar can be further customized in various ways. Firstly, if you want a more dark navbar replace the `.navbar-default` class with `.navbar-inverse`. Or if you want the navbar to be constantly fixed to the top of the webpage regardless of where the user has scrolled to, add the `.navbar-fixed-top` class.

The Bootstrap navbar is responsive & mobile-friendly by default. Try resizing your browser's width and see how your navbar changes.

Read more about Bootstrap's navbar [here](http://getbootstrap.com/components/#navbar).


## Bonus - Glyphicons
What are glyphicons you ask? Bootstrap comes with a comprehensive set of free icons (smaller than [Font Awesome](https://fortawesome.github.io/Font-Awesome/) though) that can be used throughout your website. You can find their entire list of icons [here](http://getbootstrap.com/components/#glyphicons).

So, how do glyphicons work? A glyphicon can be added like below where `X` represents the icon name:

```html
<span class="glyphicon glyphicon-X"></span>
```

Let's try adding a couple glyphicons to the navbar we just created. Try adding them to the links on the navbar like below:

```html
<ul class="nav navbar-nav">
    <li><a href="#text_row"><span class="glyphicon glyphicon-fire"></span> Text Row</a></li>
    <li><a href="#img_row"><span class="glyphicon glyphicon-leaf"></span> Image Row</a></li>
</ul>
```


## Task ∞ - This Is Not The End
We have just covered a few features out of the many, many features that has made Bootstrap a primary tool for most front-end developers. You can find out more about the [components](http://getbootstrap.com/components/), [CSS](http://getbootstrap.com/css/) & [JavaScript](http://getbootstrap.com/javascript/) of Bootstrap on their [website](http://getbootstrap.com). I would also highly recommend a lot of the online courses available on websites like edX & CodeAcademy to further your knowledge. Alternatively, play around with Bootstrap on your own and head to [StackOverflow](http://stackoverflow.com/) or [w3schools](http://www.w3schools.com/) whenever you hit a wall.

Additionally, you can jumpstart your website by using a template or theme from [here](http://startbootstrap.com), [here](https://wrapbootstrap.com) or [here](http://bootstrapbay.com/themes).

*P.S.: Bootstrap v4.0 should be releasing soon!*