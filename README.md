# JS-Challenge-Day-5 
## Flex Panels Image Gallery
a pretty snazzy animated panel that expands each section 'onClick' and back out 'onClick' again. You can even have multiple enlarged at the same time. A bit of Flex action + JS obviously

![Screenshot](flex3.png)

Here is the whole lot


      <!DOCTYPE html>
      <html lang="en">
      <head>
        <meta charset="UTF-8">
        <title>Flex Panels 💪</title>
        <link href='https://fonts.googleapis.com/css?family=Zeyada' rel='stylesheet' type='text/css'>
      </head>
      <body>
        <script type="text/javascript" src="bundle.js"></script>

        <style>
          html {
            box-sizing: border-box;
            background:#ffc600;
            font-family:'Zeyada';
            font-size: 20px;
          }
          body {
            margin: 0;
          }
          *, *:before, *:after {
            box-sizing: inherit;
          }
          .panels {
            min-height:100vh;
            overflow: hidden;
            display: flex;
          }
          .panel {
            background:#6B0F9C;
            box-shadow:inset 0 0 0 5px rgba(255,255,255,0.1);
            color:white;
            text-align: center;
            align-items:center;
            /* Safari transitionend event.propertyName === flex */
            /* Chrome + FF transitionend event.propertyName === flex-grow */
            transition:
              font-size 0.7s cubic-bezier(0.61,-0.19, 0.7,-0.11),
              flex 0.7s cubic-bezier(0.61,-0.19, 0.7,-0.11),
              background 0.2s;
            font-size: 20px;
            background-size:cover;
            background-position:center;
            flex: 1;
            justify-content: center;
            align-items: center;
            display: flex;
            flex-direction: column;
          }
          .panel1 { background-image:url(jump.png); }
          .panel2 { background-image:url(violin.png); }
          .panel3 { background-image:url(heart.png); }
          .panel4 { background-image:url(hand.png); }
          .panel5 { background-image:url(light.png); }

          .panel > * {
            margin:0;
            width: 100%;
            transition:transform 0.5s;
            flex: 1 0 auto;
            display: flex;
            justify-content: center;
            align-items: center;
          }

          .panel > *:first-child { transform: translateY(-100%);}
          .panel.open-active > *:first-child { transform: translateY(0);}
          .panel > *:last-child { transform: translateY(100%);}
          .panel.open-active > *:last-child { transform: translateY(0);}

          .panel p {
            text-transform: uppercase;
            font-family: 'Zeyada', cursive;
            text-shadow:0 0 4px rgba(0, 0, 0, 0.72), 0 0 14px rgba(0, 0, 0, 0.45);
            font-size: 2em;
          }
          .panel p:nth-child(2) {
            font-size: 4em;
          }
          .panel.open {
            flex: 5;
            font-size:40px;
          }
           </style>


        <div class="panels">
          <div class="panel panel1">
            <p>Hey</p>
            <p>Let's</p>
            <p>Dance</p>
          </div>
          <div class="panel panel2">
            <p>Give</p>
            <p>Take</p>
            <p>Receive</p>
          </div>
          <div class="panel panel3">
            <p>Experience</p>
            <p>It</p>
            <p>Today</p>
          </div>
          <div class="panel panel4">
            <p>Give</p>
            <p>All</p>
            <p>You can</p>
          </div>
          <div class="panel panel5">
            <p>Life</p>
            <p>In</p>
            <p>Motion</p>
          </div>
        </div>

      <script>
      const panels = document.querySelectorAll('.panel1, .panel2, .panel3, .panel4, .panel5');

      function toggleOpen() {
        this.classList.toggle('open');
      }

      function toggleActive(e) {
        console.log(e.propertyName);
        if(e.propertyName.includes('flex')) {
          this.classList.toggle('open-active');
        }
      }

      panels.forEach(panel => panel.addEventListener('click', toggleOpen));
      panels.forEach(panel => panel.addEventListener('transitionend', toggleActive));

      </script>

      </body>
      </html>

![Screenshot](flex2.png)
![Screenshot](flex4.png)
