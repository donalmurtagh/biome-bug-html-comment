Reproduces a bug in Biome that causes the formatter to fail if the file contains HTML elements nested in HTML comments. 

## Instructions

Follow these steps to reproduce this issue:

 - Download this repository
 - Run `yarn install`
 - Run `yarn biome format --write`

## Cause

The cause of the issue is the HTML element nested inside the HTML comment in `src/app.vue`

```
  <div>
    <!--
    The script element in this comment causes a formatter failure <script>
    -->
  </div>
```

Curiously, the bug does not occur if the comment is changed to either of the following

```
  <div>
    <!-- The script element in this comment causes a formatter failure <script> -->
  </div>
```
```
  <div>
    <!--
    The script element in this comment causes a formatter failure <div>
    -->
  </div>
```
