---

title: A Javascript Experiment - Movement
slug: a-javascript-experiment-movement
summary: A prototype library for generating moveable tile-based interfaces for fun and profit

date: 2006-04-02T00:00:00+00:00
location: London, UK

---

After a friday spent researching alternative interfaces, (after being challenged by [James][5]), I've developed a nice little Javascript class which allows you to re-create a popular shifting effect, used to great effect on sites such as [One Digital][1]. I've created [an example of the script][2] in action showing the London tube map being shifted around.

Install the Javascript object using the following code. The parameters passed are the name of the `div` you wish to shift and the number of horizontal/vertical stops in the grid. The Javascript deals with moving the target `div` into the middle of the page so alternative styling can be used if Javascript is not available. It also divides the page up into a grid of 'stops’ for navigating around.

    <script type="text/javascript" src="includes/js/prototype.js"></script>
    <script type="text/javascript" src="includes/js/movement.js"></script>
    <script type="text/javascript">
      movement = new Movement("shiftMe", 9, 6);
    </script>

The <acronym title="Cascading Style Sheets">CSS</acronym> is fairly self-explanatory. The target `div` needs to be given a width and height to be divided up but the nav can be styled however you want.

    div {
      background: transparent url("../images/bg-content.gif") 0 0 no-repeat;
      border: solid 3px #27B1E6;
      height: 2048px;
      position: absolute;
      width: 3074px;
    }

The script uses [prototype][3], (as all good Javascripts do), and has been tested and works in <acronym title="Internet Explorer">IE</acronym> 6, <acronym>IE</acronym> 7 Beta 2, Firefox and Safari. [Download it and have a play][4].

[1]: http://www.1digital.com.br/sitevs2/1digital.html
[2]: https://github.com/beseku/prototype.movement/
[3]: http://prototype.conio.net/
[4]: https://github.com/beseku/prototype.movement/
[5]: http://jeckecko.net