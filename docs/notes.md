---
icon: lucide/rocket
---

# Time-series Notes

## Intro

Time series is a dataset where the elements follow a sequential order due to a time variable.

Predicting future values of a time series is called forecasting.

Trends and patterns may be seasonal or cyclical.

Example:

<div style="text-align: center;">
  <img src="https://i0.wp.com/statisticsbyjim.com/wp-content/uploads/2020/07/TimeSeriesTrade.png?fit=576%2C384&amp;ssl=1" alt="Time Series Analysis Introduction - Statistics By Jim"/>
</div>

## Uses and types

The uses for Time-Series analysis are:

1. Forecasting
2. Anomaly detection


>Time series typically involve stochastic processes i.e., processes that evolve over time in a random and unpredictable manner.

When modelling time series data the data falls into two categories:

- **Signals:** Trends, seasonality, and cycles

- **Noise/Residuals:** Other data which may/may not be random

https://www.geeksforgeeks.org/machine-learning/time-series-analysis-and-forecasting/

There are various types of time-series forecasting methods:

- **Univariate:** Only tracks one variable with respect to time
- **Multivariate:** Tracks several related variables and understand how they effect each other over time

- **Continous:** Observations are at every moment at a very high frequency, i.e., ECG data
- **Discrete:** Observations that are at set intervals i.e., hourly, daily etc.

- **Stationary:** Series which has a constant mean, variance, and pattern, with no trend or seasonality
- **Non-stationary:** Series where the above changes

## Data Analytics Lifecycle

3. **Model Planning:** Study relationships between the important measures, and determine the best model
4. **Model Building:** Develop datasets to test and train models, and execute these models
5. **Communicate Results:** Communicate the findings, and quantify the business value


### Discovery

Frame initial business problem and make initial hypothesis.

1. **Assess the resources available to the project:** People, technology, time, and data
2. **Learning the business domain:** This includes the history (Have similar projects been attempted before at the org?)
3. **Frame the problem and formulate hypothesis:** This will be tested using the data

### Data Preparation

Familiarise yourself with the data, transform, and clean data.

#### Graphs and notation

Best way to make sense of time-series data is by plotting it.

When forecasting: It is important data is in order chronologically (by time) and evenly spaced out. One important assumption for forecasting to work is that datapoints have some dependency to each other.

When doing forecasting - the independent time variable is the index, and is on the x-axis.

The dependent variable being looked at, y is on the y-axis. The subscript t is added to this to refer to the value of the dependent variable at a particular moment in time.



#### Datetime index

#### Plotting, slicing, resampling time-series

#### Handling outliers and missing values








## Examples

### Admonitions

> Go to [documentation](https://zensical.org/docs/authoring/admonitions/)

!!! note

    This is a **note** admonition. Use it to provide helpful information.

!!! warning

    This is a **warning** admonition. Be careful!

### Details

> Go to [documentation](https://zensical.org/docs/authoring/admonitions/#collapsible-blocks)

??? info "Click to expand for more info"

    This content is hidden until you click to expand it.
    Great for FAQs or long explanations.

## Code Blocks

> Go to [documentation](https://zensical.org/docs/authoring/code-blocks/)

``` python hl_lines="2" title="Code blocks"
def greet(name):
    print(f"Hello, {name}!") # (1)!

greet("Python")
```

1.  > Go to [documentation](https://zensical.org/docs/authoring/code-blocks/#code-annotations)

    Code annotations allow to attach notes to lines of code.

Code can also be highlighted inline: `#!python print("Hello, Python!")`.

## Content tabs

> Go to [documentation](https://zensical.org/docs/authoring/content-tabs/)

=== "Python"

    ``` python
    print("Hello from Python!")
    ```

=== "Rust"

    ``` rs
    println!("Hello from Rust!");
    ```

## Diagrams

> Go to [documentation](https://zensical.org/docs/authoring/diagrams/)

``` mermaid
graph LR
  A[Start] --> B{Error?};
  B -->|Yes| C[Hmm...];
  C --> D[Debug];
  D --> B;
  B ---->|No| E[Yay!];
```

## Footnotes

> Go to [documentation](https://zensical.org/docs/authoring/footnotes/)

Here's a sentence with a footnote.[^1]

Hover it, to see a tooltip.

[^1]: This is the footnote.


## Formatting

> Go to [documentation](https://zensical.org/docs/authoring/formatting/)

- ==This was marked (highlight)==
- ^^This was inserted (underline)^^
- ~~This was deleted (strikethrough)~~
- H~2~O
- A^T^A
- ++ctrl+alt+del++

## Icons, Emojis

> Go to [documentation](https://zensical.org/docs/authoring/icons-emojis/)

* :sparkles: `:sparkles:`
* :rocket: `:rocket:`
* :tada: `:tada:`
* :memo: `:memo:`
* :eyes: `:eyes:`

## Maths

> Go to [documentation](https://zensical.org/docs/authoring/math/)

$$
\cos x=\sum_{k=0}^{\infty}\frac{(-1)^k}{(2k)!}x^{2k}
$$

!!! warning "Needs configuration"
    Note that MathJax is included via a `script` tag on this page and is not
    configured in the generated default configuration to avoid including it
    in a pages that do not need it. See the documentation for details on how
    to configure it on all your pages if they are more Maths-heavy than these
    simple starter pages.

<script id="MathJax-script" src="https://unpkg.com/mathjax@3/es5/tex-mml-chtml.js"></script>
<script>
  window.MathJax = {
    tex: {
      inlineMath: [["\\(", "\\)"]],
      displayMath: [["\\[", "\\]"]],
      processEscapes: true,
      processEnvironments: true
    },
    options: {
      ignoreHtmlClass: ".*|",
      processHtmlClass: "arithmatex"
    }
  };

  document$.subscribe(() => {
    MathJax.startup.output.clearCache()
    MathJax.typesetClear()
    MathJax.texReset()
    MathJax.typesetPromise()
  })
</script>

## Task Lists

> Go to [documentation](https://zensical.org/docs/authoring/lists/#using-task-lists)

* [x] Install Zensical
* [x] Configure `zensical.toml`
* [x] Write amazing documentation
* [ ] Deploy anywhere

## Tooltips

> Go to [documentation](https://zensical.org/docs/authoring/tooltips/)

[Hover me][example]

  [example]: https://example.com "I'm a tooltip!"
