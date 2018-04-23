# TechDegree Project 1  - Random Quotes

# main index.html, normalize.css, styles.css and script.js

the entire app was tested on the following browsers
  latest release of macOS Safari and Chrome
  latest release of Windows10 Edge and Chrome
  latest release of iOS Safari on iPhone 6 and iPad Air

  most of the basic html and css that was provided was used
    with some changes outlined below
      to allow for more responsive browsing experience on mobile device and PC/MAC internet browsers
      some tweaks to padding, margins, font and alignment were made
        to try to make the most of screen space provided by various devices and computers

# the main app

  the main app is run by js/scripts.js

  the scripts.js calls the printQuote function once
    so a random Quote and background color will appear when the index.html page first loads

  the #loadQuote button element is selected and assigned to a const variable in printQuote.js

  the eventListener to the #loadQuote button otherwise unchanged
    once the #loadQuote button is "clicked"
    it then calls the printQuote function

# CSS and HTML layout changes

    moved style of #quote-box for position, top, left, right and width
        to .container
          elements with-in .container div, including #loadQuote button...
          appear to move when width and height of web page adjusted
          these keep position and spacing relative to each other

    since a random background-color is set to entire body element and #loadQuote button
      font color and border color of is elements set to black
      so text and borders are more readable and reduce any "neon" or reflective affect

    added styling for a .tag element for quote object's tag property

    added meta tag name=viewport, for RWD, to index.html
    and tweaked styling of .container div elements and sub-elements
      for mobile devices using @media (max-width: 420px)

# Quotes and colors array

    quotes and colors array found in js/data.js

    quotes array
      is array of 10 quote objects
      each quote has a quote, source property
      optionally, some quotes have a citation, year and tag property
      the year propety is a date stored as an integer in milliseconds counting before or past Jan. 1, 1970

    colors array
      is an array of 10 color strings
      each color is a hex color string

# the getRandomQoute function

    the getRandomQoute found in js/getRandom.js

      the previous random number (randomQuoteNumber
          is pushed onto the end of the randomQuoteArray

      to get a new random Number
        math.Random() * object-array.length is used to get a random float value
        math.Floor() then rounds down, removing any decimal values

      an if/else conditional evaluates the value in the previous number and new random number
          if the new random number DO NOT match the previous number
            then the new random number is returned
          if the previous and new random numbers DO match
            then get another random number and return it

      the randomQuoteNumber is used as an index
          to return a quote object from the quotes array
          ... return quotes[randomQuoteNumber]

# the getRandomColor function

    the same process implemented in getRandomQoute is used to get a random color
        using a randomColorNumber and randomColorArray
          ... return colors[randomColorNumber]


# printQuote function

    found in js/printQuote.js

    before the printQuote function actually runs is called...
      selection of the body, .quote-body, #loadQuote elements and assigned these to respective variables
      a myInterval values is set to 30000
        these variables are declared and initialized here because the printQuote function requires them
        but the printQuote function must be loaded before the scripts.js is loaded

    after printQuote is called
      a clearInterval(myInterval) runs clearing or resets the interval
      getRandomQuote is called, storing the returned random quote object in a displayQuote var
      getRandomColor is called, storing the returned random color string in a displayColor var

      the random quote object properties, displayQuote.quote, .source
          are concatenated into html string with appropriate html tags

      if the .citation, .year and .tag properties exist these are
          also concatenated into html string with appropriate html tags
          the .year is a date stored as an integer
            which is a date in milliseconds before or since Jan, 1st 1970
            using Date() and .getFullYear()
            the .year property is converted back into a readable date string

      the completed html String is printed to the quote-box div using innerHTML()

      the random color string is concatenated and assigned directly to the body and loadQuote style attributes

       myInterval is set back to 30 secs using setInterval(myInterval, 30000)
