## Network and Web Security

---

## Preamble
1. <em>A system is secure if it behaves precisely in the manner intended -- and does nothing more.</em>; **Ivan Arce** - A renowned vulnerability hunter, circa 2000.
2. <em> A system is secure if and only if it starts in a secure state and cannot enter an insecure state.</em>; **Bella-La Padula** security model - 1960.
3. <em>A system is secure if it adequately protects information that it processes against unauthorized discolusre, unauthorized modification, and unauthorized witholding</em>.
---

## Background
1. The Web has been plagued by a perplexing number, and a remarkable variety of security issues.
2. Security flaws attributed to poor client or server implementations and arbitrary design decisions.
3. Breakdown of the Client-Server Divide; The culprit is **__Javascript__**, a language theat offers the HTTP servers a way to delegate application logic to the browser ("client") side.
---

## Presentation Outline
1. Browser-Side Scripts.
2. Non-HTML Document Types.
3. Content Rendering with Browser Plugins.
4. New and Upcoming Security Features.
---

## Browser-Side Scripts
---

### Browser-Side Scripts
<img src='./images/mocha_js.png'/>
---

### Basic Characteristics of Javascript
1. C-influenced syntax.
2. A straightforward classless object model **??**
3. Automatic garbage collection.
```js
var text = "Hi mom!";
function display_string(str) {
  alert(str);
  return 0;
}
// This will display "Hi mom!". display_str(text);
display_str(text);
```
---

#### Script Processing Model
1. Every HTML document displayed in a browser is given a separate instance of the Javascript execution environment; with an individual namespace for all global variables and functions crated by the loaded scripts.
2. Within a particular execution context, all encountered JavaScript blocks are processed individually and almost always in a well-defined order.
---

#### Parsing
The parsing stage validates the syntax of the script block.

Example 1:
```js
<script>
var my_variable1 = 1;
var my_variable2 =
</script>

<script>
2;
</script>
```

Example 2:
```js
<script>
var my_variable1 = 1;
var my_variable2 = 2;
</script>
```
---

#### Function Resolution
Example 1:
```js
<script>
hello_world();

function hello_world(){
  alert('Hi mom!');
}
</script>
```

Example 2:
```js
<script>
 hello_world();
</script>

<script>
function hello_world(){
 alert('Hi mom!');
}
</script>
```
---

#### Code Execution
```js
<script>
function not_called() {
 return 42;
}

function hello_world() {
 alert("With this program, anything is possible!"); 
 do_stuff();
}

alert("Welcome to our demo application.");

hello_world();
</script>
```
---

#### Code and Object Inspection Capabilities
1. `eval(...)` function.
    ```js
        eval("alert('Hi mom!')");
    ```
2. `setTimeout`, `setInterval`, `onClick`, `document.write(...)`

<blockquote>Modification of runtime environment.</blockquote>
---

#### Browser API features
1. _**location**_ object.
2. _**history**_ object.
3. _**screen**_ object.
4. _**navigator**_ object.
5. _**document**_ object.
---

#### Non-HTML Document Types
1. Plaintext files: **_Content-Type: text/plain_**
2. Bitmap Images: JPEG, PNG, GIF, BMP; e.g. **_Content-Type: image/jpeg_**
3. Audio and Video
4. XML-Based Documents.
```xml
<foo xmlns="http://www.example.com/nonexistent"> 
  <u>Hello</u>
  <html xmlns="http://www.w3.org/1999/xhtml">
     <u>world!</u>
  </html>
</foo>
```
5. Scalar Vector Graphics (SVG).
6. Mathematical Markup Languages.
7. Really Simple Syndication (RSS) and Atom Feeds.
---

#### Content Rendering with Browser Plugins
