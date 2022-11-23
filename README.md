# plotlyhs 

A Haskell library for data visualization, using [Plotly.js](https://plotly.com/javascript/). Generate interactive charts in HTML from your Haskell data.

This basically creates JSON data which can be read by Plotly.js. 

Note: this is my fork of plotlyhs, which adds a few extra features to the library begun by @glutamate. This is the most well-maintained fork, as far as I know, and the fork you'll see up [here on hackage](https://hackage.haskell.org/package/plotlyhs-0.2.1). 

[Find the documentation here on Hackage.](https://hackage.haskell.org/package/plotlyhs-0.2.1/docs/Graphics-Plotly.html)

## Example

For more, [see the examples page](https://JonathanReeve.github.io/plotlyhs/)

```haskell
{-# LANGUAGE OverloadedStrings #-}

import Lucid
import Lucid.Html5
import Graphics.Plotly
import Graphics.Plotly.Lucid
import Lens.Micro

import qualified Data.Text.Lazy as T
import qualified Data.Text.Lazy.IO as T

main =
  T.writeFile "test.html" $ renderText $ doctypehtml_ $ do
    head_ $ do meta_ [charset_ "utf-8"]
               plotlyCDN
    body_ $ toHtml $ plotly "myDiv" [myTrace]

myTrace = scatter & x ?~ [1,2,3,4]
                  & y ?~ [500,3000,700,200]
```
