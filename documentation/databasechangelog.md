---
layout: default
title: Databasechangelog
---

# Database Change Log File

The root of all Liquibase changes is the databaseChangeLog file.

## Available Attributes ##

<table>
<tr><th>Attribute</th><th>Description</th></tr>
<tr><td>logicalFilePath</td><td>Use to override the file name and path when creating the unique identifier of change sets. Required when moving or renaming change logs.</td></tr>
</table>

## Available Sub-Tags ##

<table>
<tr><th>Tag</th><th>Description</th></tr>
<tr><td>preConditions</td><td>Pre-conditions required to execute the change log. <a href="preconditions.html">Read More</a></td></tr>
<tr><td>property</td><td>Value to set property to, if not set by another means. <a href="changelog_parameters.html">Read More</a></td></tr>
<tr><td>changeSet</td><td>The change sets to execute. <a href="changeset.html">Read More</a></td></tr>
<tr><td>include</td><td>Additional files containing change sets to execute. <a href="include.html">Read More</a></td></tr>
</table>

When the Liquibase migrator runs, it parses the databaseChangeLog tag. It first checks any preconditions specified. If any of the [preconditions](preconditions.html) fail, the Liquibase will exit with an error message explaining what failed. Preconditions are useful for both documenting and enforcing expectations and assumptions of the changelog writer such as the DBMS to be run against or the user the changes are run as.

If all preconditions are met, Liquibase will then begin running [changeSet](changeset.html) and [include](include.html) tags **in the order they appear in the databaseChangeLog file**.

The XML schema for the databaseChangeLog tag is available at:

* [http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-3.6.xsd](http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-3.6.xsd) **Since 3.6**

Some legacy XSDs are listed on [the XML Format page](xml_format.html).

Each changeSet contains an "id" tag and an "author" tag. These tags, along with the classpath location and name of the XML file create a unique identifier for that changeSet.

## Sample Empty Change Log ##

<div id='changelog-tabs'>
<ul>
    <li><a href="#tab-xmlv3">XML Format</a></li>
    <li><a href="#tab-yaml">YAML Format</a></li>
    <li><a href="#tab-json">JSON Format</a></li>
    <li><a href="#tab-sql">SQL Format</a></li>
  </ul>

<div id="tab-xmlv3">
{% highlight xml %}
<databaseChangeLog
    xmlns="http://www.liquibase.org/xml/ns/dbchangelog"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xmlns:ext="http://www.liquibase.org/xml/ns/dbchangelog-ext"
    xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-3.6.xsd
    http://www.liquibase.org/xml/ns/dbchangelog-ext http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-ext.xsd">
</databaseChangeLog>
{% endhighlight %}
</div>

<div id="tab-yaml">
{% highlight yaml %}
databaseChangeLog:
{% endhighlight %}
</div>

<div id="tab-json">
{% highlight json %}
{
    "databaseChangeLog": [
    ]
}

{% endhighlight %}
</div>

<div id="tab-sql">
{% highlight sql %}
--liquibase formatted sql

{% endhighlight %}
</div>
</div>

<script>
  $(function() {
    $( "#changelog-tabs" ).tabs();
  });
</script>
