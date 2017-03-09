---
layout: post
title: Jekyll 日期格式
categories: Jekyll
tags: Jekyll 语法
description: Jekyll Date Formatting
---


转至 [http://alanwsmith.com/jekyll-liquid-date-formatting-examples](http://alanwsmith.com/jekyll-liquid-date-formatting-examples)



---
### Overview
{{ page.date }}  
2013-11-29 00:00:00 -0500


{{ page.date | date: '%B %d, %Y' }}  
November 29, 2013


### Built-in Jekyll Date Filters
  ● Date to String
  
{{ page.date | date_to_string }}  
Output Example 1: 03 May 2013  
Output Example 2: 04 Jul 2013  
Output Example 3: 23 Sep 2013  
Output Example 4: 26 Nov 2013  

  ● Date to Long String
  
{{ page.date | date_to_long_string }}  
Output Example 1: 03 May 2013  
Output Example 2: 04 July 2013  
Output Example 3: 23 September 2013  
Output Example 4: 26 November 2013  

  ● Date to XML Schema
  
{{ page.date | date_to_xmlschema }}  
Output Example 1: 2013-05-03T09:14:00-04:00  
Output Example 2: 2013-07-04T09:14:00-04:00  
Output Example 3: 2013-09-23T09:14:00-04:00  
Output Example 4: 2013-11-26T08:14:00-05:00  

  ● Date to RFC-822
  
{{ page.date | date_to_rfc822 }}  
Output Example 1: Fri, 03 May 2013 09:14:00 -0400  
Output Example 2: Thu, 04 Jul 2013 09:14:00 -0400  
Output Example 3: Mon, 23 Sep 2013 09:14:00 -0400  
Output Example 4: Tue, 26 Nov 2013 08:14:00 -0500  

### Liquid Jekyll Date Formatting Examples
  ● ISO 8601 Date5
  
{{ page.date | date: "%Y-%m-%d" }}  
Output Example 1: 2013-05-03  
Output Example 2: 2013-07-04  
Output Example 3: 2013-09-23  
Output Example 4: 2013-11-26  

  ● U.S. Numeric Style with Four Digit Years (With leading zeros.)
  
{{ page.date | date: "%m/%d/%Y" }}  
Output Example 1: 05/03/2013  
Output Example 2: 07/04/2013  
Output Example 3: 09/23/2013  
Output Example 4: 11/26/2013  

  ● U.S. Numeric Style with Four Digit Years (Leading zeros removed.)
  
{{ page.date | date: "%-m/%-d/%Y" }}  
Output Example 1: 5/3/2013  
Output Example 2: 7/4/2013  
Output Example 3: 9/23/2013  
Output Example 4: 11/26/2013  

  ● U.S. Numeric Style with Two Digit Year (Leading zeros removed.)
  
{{ page.date | date: "%-m/%-d/%y"}}  
Output Example 1: 5/3/13  
Output Example 2: 7/4/13  
Output Example 3: 9/23/13  
Output Example 4: 11/26/13 

  ● Outside U.S. Style with Full Month Name (Leading zeros removed.)
  
{{ page.date | date: "%-d %B %Y"}}  
Output Example 1: 3 May 2013  
Output Example 2: 4 July 2013  
Output Example 3: 23 September 2013  
Output Example 4: 26 November 2013  

  ● Outside U.S. Style with Non-English Full Month Name (Leading zeros removed.)
  
This example uses the German names for months. Any other language can be used by simply substituting the proper names for each month.

<!-- Whitespace added for readability -->

    {% assign m = page.date | date: "%-m" %}
    {{ page.date | date: "%-d" }}
    {% case m %}
      {% when '1' %}Januar
      {% when '2' %}Februar
      {% when '3' %}M&auml;rz
      {% when '4' %}April
      {% when '5' %}Mai
      {% when '6' %}Juni
      {% when '7' %}Juli
      {% when '8' %}August
      {% when '9' %}September
      {% when '10' %}Oktober
      {% when '11' %}November
      {% when '12' %}Dezember
    {% endcase %}
    {{ page.date | date: "%Y" }}

Output Example 1: 3 Mai 2013  
Output Example 2: 4 Juli 2013  
Output Example 3: 23 September 2013  
Output Example 4: 26 November 2013 

  ● U.S. Style with Full Month Name (Leading zeros removed.)
  
{{ page.date | date: "%B %-d, %Y" }}  
Output Example 1: May 3, 2013  
Output Example 2: July 4, 2013  
Output Example 3: September 23, 2013  
Output Example 4: November 26, 2013  

  ● U.S. Style with Full Month Names and Ordinalized Days (Leading zeros removed.)
  
<!-- Whitespace added for readability -->

    {% assign d = page.date | date: "%-d"  %}
    {{ page.date | date: "%B" }} 
    {% case d %}
      {% when '1' or '21' or '31' %}{{ d }}st
      {% when '2' or '22' %}{{ d }}nd
      {% when '3' or '23' %}{{ d }}rd
      {% else %}{{ d }}th
      {% endcase %}, 
    {{ page.date | date: "%Y" }}

Output Example 1: May 3rd, 2013  
Output Example 2: July 4th, 2013  
Output Example 3: September 23rd, 2013  
Output Example 4: November 26th, 2013  

  ● U.S. Style with AP Month Abbreviations and Ordinalized Days (Leading zeros removed.)
  
<!-- Whitespace added for readability -->

    {% assign d = page.date | date: "%-d" %} 
    {% assign m = page.date | date: "%B" %} 
    
    {% case m %}
      {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
      {% when 'September' %}Sept.
      {% else %}{{ page.date | date: "%b" }}.
      {% endcase %}
    {% case d %}
      {% when '1' or '21' or '31' %}{{ d }}st
      {% when '2' or '22' %}{{ d }}nd
      {% when '3' or '23' %}{{ d }}rd
      {% else %}{{ d }}th
      {% endcase %}, 
    {{ page.date | date: "%Y" }}

Output Example 1: May 3rd, 2013  
Output Example 2: July 4th, 2013  
Output Example 3: Sept. 23rd, 2013  
Output Example 4: Nov. 26th, 2013  

  ● U.S. Style Full Day and Full Month Names (Leading zeros removed.)
  
{{ page.date | date: "%A, %B %-d, %Y" }}
Output Example 1: Friday, May 3, 2013  
Output Example 2: Thursday, July 4, 2013  
Output Example 3: Monday, September 23, 2013  
Output Example 4: Tuesday, November 26, 2013  

  ● Chicago Manual of Style Day Abbreviations and U.S. Style Date (With "Thurs." and "Tues.")
  
<!-- Whitespace added for readability -->

    {% assign dy = page.date | date: "%a" %}
    {% case dy %}
      {% when "Tue" %}Tues
      {% when "Thu" %}Thurs
      {% else %}{{ dy }}
      {% endcase %}. 
    ~
    {{ page.date | date: "%B" }} 
    {{ page.date | date: "%-d" }}, 
    {{ page.date | date: "%Y" }}

Output Example 1: Fri. ~ May 3, 2013  
Output Example 2: Thurs. ~ July 4, 2013  
Output Example 3: Mon. ~ September 23, 2013  
Output Example 4: Tues. ~ November 26, 2013  

### Individual Component Snippets for Liquid Date Formatting

  ● Numeric Month with Leading Zeros Removed
  
{{ page.date | date: "%-m" }}

  ● Numeric Day with Leading Zeros Removed
  
{{ page.date | date: "%-d" }}

  ● Ordinalized Numeric Day with Leading Zeros Removed
  
    {% assign d = page.date | date: "%-d" %}
    {% case d %}
      {% when '1' or '21' or '31' %}{{ d }}st
      {% when '2' or '22' %}{{ d }}nd
      {% when '3' or '23' %}{{ d }}rd
      {% else %}{{ d }}th
      {% endcase %}

  ● AP Style Month Abbreviations
  
    {% assign m = page.date | date: "%B" %}
    {% case m %}
      {% when 'April' or 'May' or 'June' or 'July' %}{{ m }}
      {% when 'September' %}Sept.
      {% else %}{{ page.date | date: "%b" }}.
      {% endcase %}

(Produces: "Jan.", "Feb.", "Mar.", "April", "May", "June", "July", "Aug.", "Sept.", "Oct.", "Nov.", "Dec.")

  ● Chicago Manual of Style Day Abbreviations
  
    {% assign dy = page.date | date: "%a" %}
    {% case dy %}
      {% when "Tue" %}Tues
      {% when "Thu" %}Thurs
      {% else %}{{ dy }}
      {% endcase %}.

(Produces: "Sun.", "Mon.", "Tues.", "Wed.", "Thurs.", "Fri.", "Sat.")

  ● Chicago Manual of Style Month Abbreviations
  
    {% assign m = page.date | date: "%B" %}
    {% case m %}
      {% when 'May' or June' or 'July' %}{{ m }}
      {% when 'September' %}Sept.
      {% else %}{{ page.date | date: "%b" }}.
      {% endcase %}

(Produces: "Jan.", "Feb.", "Mar.", "Apr.", "May", "June", "July", "Aug.", "Sept.", "Oct.", "Nov.", "Dec.")

  ● Non-English Month Names
  
    {% assign m = page.date | date: "%-m" %}
    {% case m %}
      {% when '1' %}Januar
      {% when '2' %}Februar
      {% when '3' %}M&auml;rz
      {% when '4' %}April
      {% when '5' %}Mai
      {% when '6' %}Juni
      {% when '7' %}Juli
      {% when '8' %}August
      {% when '9' %}September
      {% when '10' %}Oktober
      {% when '11' %}November
      {% when '12' %}Dezember
    {% endcase %}

(Produces: "Januar", "Febuar", "März", "April", "Mai", "Juni", "Juli", "August", "September", "Oktober", "November", "Dezember")

--------------------------------------------------------------------------------
Notes on the Examples
  1. The hour, minute and second parts of the full date/time stamp aren't being used because Jekyll tends to zero them out.
  2. In some of the examples, the code is split to multiple lines to help readability. If it's a natural break point where white space already exists, this won't effect HTML rendering. In some cases, it will introduce unwanted white space. Simply move everything back to one line to create the desired presentation.
  3. Since the original version of this post went up, updates have been made to use the cleaner version of {{ page.date | date: "%-m" }} instead of {{ page.date | date: "%m" | plus:'0' }} and {{ page.date | date: "%-d" }} instead of {{ page.date | date: "%d" | plus:'0' }} to remove leading zeros.
  4. An additional update was made to add an example for non-English month names.
Footnotes
  1. These examples were create on a Mac running OS X 10.8.5 with: Ruby 2.0.0p247 - Jekyll 1.2.1 - liquid 2.5.2. Your mileage may vary.
  2. The main Jekyll website provides a great overview of the software. You can learn even more with a visit to the Jekyll's GitHub Repo.
  3. Shopify's Liquid template engine. "A small and fast template language which is quick to learn but very powerful for full customization."
  4. The Liquid Date Filter offers some basic formatting elements and is the basis of these code snippets. Note that in some cases "post.date" might be required instead of "page.date".
  5. Observant readers will notice that as of the time this post went live, my design still uses a date format with leading zeros. I have the solution, it just hasn't been implement yet. It'll go in with the next set of design changes.
  6. ISO 8601 - "Data elements and interchange formats - Information interchange - Representation of dates and times is an international standard covering the exchange of date and time-related data." A perfect example of how Time really is wibbly wobbly timey wimey… stuff.