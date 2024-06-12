# Zoning Analysis and Predictive Model of Customers Affected in a Power Outage

### Created by Samuel Mahjouri and Zoya Hasan

## Introduction

Power outages pose significant risks to the safety, economy, and daily life of U.S. citizens, making it imperative to understand the factors that influence their duration and impact. Our  analysis utilizes a dataset on major power outage events in the continental U.S. from January 2000 to July 2016, provided by Mukherjee, Nateghi, and Hastak from Purdue University. The dataset includes information on geographical location, regional climatic conditions, land-use characteristics, regional electricity consumption patterns, and economic attributes of power outages in various states. Given such a holistic understanding of power outages, we posed the question that could support energy companies when considering where to aid during power outages. Our key question is: What are the key factors that influence the durations of major power outages in the continental U.S., and how can these insights be used to mitigate future outages? This question holds practical implications for utility companies, as well as regional communities. By identifying the determinants of outage durations, energy companies  can better prepare for and respond to future incidents. Given the increasing number and high severity of weather-related disruptions, understanding these dynamics, in correlation to power outages, is more critical than ever. The dataset used in this project has 1534 rows and 56 columns, and offers comprehensive insight to uncover our questions through data analysis. The dataset encompasses information on every major power outage in the United States from 2000 to 2016. Only a handful of columns were used for analysis and prediction, as described below:

---
layout: default
---

Authors: **Samuel Mahjouri and Zoya Hasan**

Text can be **bold**, _italic_, or ~~strikethrough~~.

[Link to another page](./another-page.html).

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![Octocat](https://github.githubassets.com/images/icons/emoji/octocat.png)

### Large image

![Branching](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

| Feature        | Description     |
|:-------------|:------------------|
| `YEAR`       | the year when the outage event occurred
 | 
| `MONTH` | the month when the outage event occurred |
| ok           | good     | 
| ok           | good `zoute` drop |

