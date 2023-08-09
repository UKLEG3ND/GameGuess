<html>
<head>
<title>Guess the Magic Number</title>
<style type="text/css">
  body {
    background: #CCCC99;
    font-family: arial;
    background-image: url("https://newton.ncc.edu/gansonj/ite154/img/casino1.jpg");
  }

  #pagewrap {
    width: 700px;
    margin: 40px auto 0px auto;
    border: 10px orange solid;
  }

  #header {
    text-align: center;
    color: #FFFFFF;
    font-weight: bold;
    font-size: 1.45em;
    background: maroon;
    padding: 20px 0px 20px 0px;
  }

  #content {
    background: #FFFFFF;
    padding: 30px;
    height: 350px;
    background-image: url("http://newton.ncc.edu/gansonj/ite154/img/qmark.png");
    background-repeat: no-repeat;
    background-position: 90% 40%;
  }

  #formtext {
    margin: 15px 0px 15px 0px;
  }

  #userguess {
    background: #CCCC99;
    width: 300px;
    padding: 8px;
    border: 2px black solid;
    border-radius: 25px;
  }

  #footer {
    background: maroon;
    color: #FFFFFF;
    height: 65px;
  }

  #guessbutton {
    background: #003366;
    color: #FFFFFF;
    padding: 5px 0px 5px 0px;
    width: 150px;
    border: 3px #CCCC99 solid;
    border-radius: 25px;
    cursor: pointer;
  }

  #guessbutton:hover {
    background: #CCCCCC;
    color: #003366;
    border: 3px #003366 solid;
  }

  #success {
    font-size: 1.25em;
    color: green;
    margin-bottom: 10px;
  }

  .donebutton {
    color: darkgray;
    background-color: lightgray;
    border: 3px darkgrey solid;
  }
</style>

<script src="https://code.jquery.com/jquery-3.4.1.min.js" integrity="sha256-CSXorXvZcTkaix6Yvo6HppcZGetbYMGWSFlBw8HfCJo=" crossorigin="anonymous"></script>
<script src="https://code.jquery.com/ui/1.12.1/jquery-ui.min.js" integrity="sha256-VazP97ZCwtekAsvgPBSUwPFKdrwD3unUfSGVYrahUqU=" crossorigin="anonymous"></script>

<script type="text/javascript">
  $(document).ready(function () {
    var magicnum = Math.floor(Math.random() * 70) + 1;
    var numguesses = 0;

    $("#guessbutton").on("click", function () {
      var userguess = parseInt($("#userguess").val());
      numguesses++;

      if (userguess > magicnum) {
        var msg = "<div>Your guess is too high</div>";
        msg += "<div>Number of guesses is " + numguesses + "</div>";
      } else if (userguess < magicnum) {
        var msg = "<div>Your guess is too low</div>";
        msg += "<div>Number of guesses is " + numguesses + "</div>";
      } else {
        var msg = "<div id='success'>You guessed the Number!!!!</div>";
        msg += "<div>The magic number was " + magicnum + "</div>";
        msg += "<div>It took you " + numguesses + " guesses</div>";

        $("#guessbutton").prop("disabled", true);
        $("#guessbutton").val("Game Over!!!!");
        $("#playdiv").show();
      }

      $("#output").html(msg);
    });

    $("#playbutton").on("click", function () {
      magicnum = Math.floor(Math.random() * 70) + 1;
      numguesses = 0;
      $("#output").html("");
      $("#guessbutton").prop("disabled", false);
      $("#guessbutton").val("Submit Guess");
      $("#playdiv").hide();
    });
  });
</script>
</head>
<body>
<div id="pagewrap">
  <div id="header">
    Guess the Magic Number<br /> Between 1 and 70
  </div>
  <div id="content">
    <form>
      <div id="formtext">Enter your guess</div>
      <div><input type="text" id="userguess"></div>
      <div style="margin-top: 20px;">
        <input type="button" value="Submit Guess" id="guessbutton">
      </div>
      <div style="margin-top: 20px; display: none;" id="playdiv">
        <input type="button" value="Play Again" id="playbutton">
      </div>
    </form>
    <div id="output"></div>
  </div>
  <div id="footer"></div>
</div>
</body>
</html>

