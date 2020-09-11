
<!doctype html>
<meta charset=utf-8>
<title>Xytho's Website</title>
<meta name=viewport content="width=device-width, initial-scale=1, maximum-scale=1">
<style>
* {
  -webkit-box-sizing: border-box;
     -moz-box-sizing: border-box;
          box-sizing: border-box;
}
body {
    background: black;
    color: white;
    font-family: MS Mincho, Hiragino Mincho ProN W3, HiraMinProN-W3, serif;
    text-align: center;
    padding: 0;
    margin: 0;
}
ruby {
    -webkit-writing-mode: vertical-rl;
    -ms-writing-mode: vertical-rl;
    writing-mode: vertical-rl;
}
rb {
    font-size: 72pt;
}
#bio {
    max-width: 250pt;
    margin: 0 auto;
}
ul {
    padding: 0;
}
li {
    list-style-type: none;
    display: inline;
}
li:not(:last-child)::after {
    content: ' ⭐️ ';
    font-size: 66%;
}
a {
    color: white;
}
a:visited {
    color: white;
}
#witch-space {
    height: 120px;
}
footer {
    margin-top: 1.33em;
}
</style>

<main>
    <h1><ruby><rb>Xytho</rb><rp>〜</rp><rt>Privacy Website</rt></ruby></h1>
    <!--twitter_bio_begin--><p id="bio">Privacy is a qualified, fundamental human right. ... United Nations Declaration of Human Rights (UDHR) 1948, Article 12: “No one shall be subjected to arbitrary interference with his privacy, family, home or correspondence, nor to attacks upon his honour and reputation.</a></p>
    <ul>
        
        <li><a href="https://github.com/Xythoo">github</a></li>
       
    </ul>
</main>

<div id=witch-space>
</div>

<footer>
© 2020
</footer>

<script>
(function () {
    'use strict';

    window.onload = function () {
        // 😭
        if (/ Firefox\/\d+\.\d+/.test(navigator.userAgent)) {
            var s = document.getElementsByTagName('rt')[0].style;
            s.left = '96pt';
            s.position = 'relative';
            s = document.getElementsByTagName('ruby')[0].style;
            s.left = '24pt';
            s.position = 'relative';
        }
        // 🤔
        if (/ Chrome\/\d+(\.\d+)*/.test(navigator.userAgent)) {
            var s = document.getElementsByTagName('ruby')[0].style;
            s.display = 'block';
            s.margin = '0 auto';
        }

        var canvas = document.createElement('canvas');
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        canvas.style.position = 'fixed';
        canvas.style.left = canvas.style.top = canvas.style.right = canvas.style.bottom = '0';
        canvas.style.zIndex = -1;
        document.body.appendChild(canvas);

        // Edge requires the experimental- prefix apparently
        var gl = canvas.getContext('webgl') || canvas.getContext('experimental-webgl');

        gl.enable(gl.BLEND);
        gl.blendFunc(gl.SRC_ALPHA, gl.ONE_MINUS_SRC_ALPHA);

        var starVertexShader = gl.createShader(gl.VERTEX_SHADER);
        gl.shaderSource(starVertexShader, document.getElementById('star-vertex-shader').textContent);
        gl.compileShader(starVertexShader);
        console.log(gl.getShaderInfoLog(starVertexShader));

        var starFragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
        gl.shaderSource(starFragmentShader, document.getElementById('star-fragment-shader').textContent);
        gl.compileShader(starFragmentShader);
        console.log(gl.getShaderInfoLog(starFragmentShader));

        var starShaderProgram = gl.createProgram();
        gl.attachShader(starShaderProgram, starVertexShader);
        gl.attachShader(starShaderProgram, starFragmentShader);
        gl.linkProgram(starShaderProgram);
        console.log(gl.getProgramInfoLog(starShaderProgram));

        var starTimeUniform = gl.getUniformLocation(starShaderProgram, "time");
        var starSpeedUniform = gl.getUniformLocation(starShaderProgram, "starSpeed");
        var starPositionAttribute = gl.getAttribLocation(starShaderProgram, "position");
        var starCenterAttribute = gl.getAttribLocation(starShaderProgram, "starCenter");
        var starProximityAttribute = gl.getAttribLocation(starShaderProgram, "starProximity");

        var witchVertexShader = gl.createShader(gl.VERTEX_SHADER);
        gl.shaderSource(witchVertexShader, document.getElementById('witch-vertex-shader').textContent);
        gl.compileShader(witchVertexShader);
        console.log(gl.getShaderInfoLog(witchVertexShader));

        var witchFragmentShader = gl.createShader(gl.FRAGMENT_SHADER);
        gl.shaderSource(witchFragmentShader, document.getElementById('witch-fragment-shader').textContent);
        gl.compileShader(witchFragmentShader);
        console.log(gl.getShaderInfoLog(witchFragmentShader));

        var witchShaderProgram = gl.createProgram();
        gl.attachShader(witchShaderProgram, witchVertexShader);
        gl.attachShader(witchShaderProgram, witchFragmentShader);
        gl.linkProgram(witchShaderProgram);
        console.log(gl.getProgramInfoLog(witchShaderProgram));

        var witchTimeUniform = gl.getUniformLocation(witchShaderProgram, "time");
        var witchScaleUniform = gl.getUniformLocation(witchShaderProgram, "scale");
        var witchCenterUniform = gl.getUniformLocation(witchShaderProgram, "witchCenter");
        var witchSizeUniform = gl.getUniformLocation(witchShaderProgram, "witchSize");
        var witchFieldUniform = gl.getUniformLocation(witchShaderProgram, "witchField");
        var witchTextureUniform = gl.getUniformLocation(witchShaderProgram, "witchTexture");
        var witchPositionAttribute = gl.getAttribLocation(witchShaderrogram, "position");

        // can't load from a data: URI because the web hates me
        var witchPixels = atob('/h//4H/+AH/gAf8B9/Af/gAf/g9/5H//g//8H//5///H//8f//D/H4fwAAAH4Pw/w+H/H4A');
        var witchWidth = 21;
        var witchHeight = 20;
        var witchWidthAligned = 24;
        var witchPixelData = new Uint8Array(witchWidthAligned * witchHeight);
        for (var i = 0; i < witchWidth * witchHeight; i++) {
            var bit = 1 & (witchPixels.charCodeAt(i >> 3) >> (7 - (i & 7)));
            var index = (i / witchWidth | 0) * witchWidthAligned + i % witchWidth;
            witchPixelData[index] = (1 - bit) * 0xFF;
        }

        var witchTexture = gl.createTexture();
        gl.bindTexture(gl.TEXTURE_2D, witchTexture);
        gl.texImage2D(gl.TEXTURE_2D, 0, gl.LUMINANCE, witchWidth, witchHeight, 0, gl.LUMINANCE, gl.UNSIGNED_BYTE, witchPixelData);
        gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MIN_FILTER, gl.NEAREST);
        gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_MAG_FILTER, gl.NEAREST);
        // non-power-of-two texture dimensions
        gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_S, gl.CLAMP_TO_EDGE);
        gl.texParameteri(gl.TEXTURE_2D, gl.TEXTURE_WRAP_T, gl.CLAMP_TO_EDGE);

        var squarePoints = [
            1, 1,
            -1, 1,
            -1, -1,
            -1, -1,
            1, -1,
            1, 1
        ];

        var starVertexData = [];
        var starVertexArray;
        var starVertexBuffer = gl.createBuffer();
        var FLOATS_PER_STAR = 3;

        var witchVertexArray = new Float32Array(squarePoints);
        var witchVertexBuffer = gl.createBuffer();
        var FLOATS_PER_WITCH_VERTEX = 2;

        gl.useProgram(witchShaderProgram);
        gl.bindBuffer(gl.ARRAY_BUFFER, witchVertexBuffer);
        gl.bufferData(gl.ARRAY_BUFFER, witchVertexArray, gl.STATIC_DRAW);

        var witchVAPs = function () {
            gl.bindBuffer(gl.ARRAY_BUFFER, witchVertexBuffer);
            gl.enableVertexAttribArray(witchPositionAttribute);
            gl.vertexAttribPointer(witchPositionAttribute, 2, gl.FLOAT, gl.FALSE, 2 * 4, 0);
        };
        witchVAPs();

        gl.uniform2f(witchSizeUniform, witchWidth, witchHeight);
        var witchSpace = document.getElementById('witch-space').getBoundingClientRect();
        gl.uniform2f(witchFieldUniform, 0, witchSpace.height);

        gl.activeTexture(gl.TEXTURE0);
        gl.bindTexture(gl.TEXTURE_2D, witchTexture);
        gl.uniform1i(witchTextureUniform, 0);

        gl.clearColor(0, 0, 0, 1);

        var starVAPs;

        window.onresize = function () {
            canvas.width = window.innerWidth;
            canvas.height = window.innerHeight;
            gl.viewport(0, 0, window.innerWidth, window.innerHeight);

            gl.useProgram(witchShaderProgram);
            gl.uniform2f(witchScaleUniform, 1 / window.innerWidth, 1 / window.innerHeight);

            gl.useProgram(starShaderProgram);
            gl.uniform1f(starSpeedUniform, (1440/canvas.width) / 8);

            var starCount = Math.floor(Math.sqrt(canvas.width * canvas.height) * 4);
            var currentStarCount = starVertexData.length / FLOATS_PER_STAR;
            if (currentStarCount < starCount) {
                for (var i = currentStarCount; i < starCount; i++) {
                    var x = Math.random() * 2 - 1, y = Math.random() * 2 - 1;
                    var r = Math.random(), g = Math.random(), b = Math.random();
                    var proximity = Math.pow(Math.random(), 4);
                    starVertexData.push(x, y);
                    starVertexData.push(proximity);
                }
            } else if (currentStarCount > starCount) {
                starVertexData.splice(starCount * FLOATS_PER_STAR);
            }

            starVertexArray = new Float32Array(starVertexData);

            gl.bindBuffer(gl.ARRAY_BUFFER, starVertexBuffer);
            gl.bufferData(gl.ARRAY_BUFFER, starVertexArray, gl.DYNAMIC_DRAW);

            starVAPs = function () {
                gl.bindBuffer(gl.ARRAY_BUFFER, starVertexBuffer);

                gl.enableVertexAttribArray(starCenterAttribute);
                gl.vertexAttribPointer(starCenterAttribute, 2, gl.FLOAT, gl.FALSE, 3 * 4, 0 * 4);

                gl.enableVertexAttribArray(starProximityAttribute);
                gl.vertexAttribPointer(starProximityAttribute, 1, gl.FLOAT, gl.FALSE, 3 * 4, 2 * 4);
            };
        };
        window.onresize();

        var initial = (new Date).getTime() / 1000;
        (function render () {
            gl.clear(gl.COLOR_BUFFER_BIT);
            gl.useProgram(starShaderProgram);
            starVAPs();
            gl.uniform1f(starTimeUniform, (new Date).getTime() / 1000 - initial);
            gl.drawArrays(gl.POINTS, 0, starVertexData.length / FLOATS_PER_STAR);
            gl.useProgram(witchShaderProgram);
            witchVAPs();
            gl.uniform1f(witchTimeUniform, (new Date).getTime() / 1000 - initial);
            var witchSpace = document.getElementById('witch-space').getBoundingClientRect();
            gl.uniform2f(witchCenterUniform, 0, 2 * (window.innerHeight / 2 - (witchSpace.top + witchSpace.height / 2)));
            gl.drawArrays(gl.TRIANGLES, 0, witchVertexArray.length / FLOATS_PER_WITCH_VERTEX);
            requestAnimationFrame(render);
        }());
    };
}());
</script>
<script type=application/glsl id=star-vertex-shader>
uniform float time;
uniform float starSpeed;
attribute vec2 starCenter;
attribute float starProximity;
void main()
{
    float effectiveTime = time * starSpeed * 2.0 * starProximity;
    vec2 calculatedCenter = vec2(mod(1.0 + (starCenter.x + effectiveTime), 2.0) - 1.0, starCenter.y);
    gl_PointSize = max(4.0 * starProximity, 0.75);
    gl_Position = vec4(calculatedCenter, 1.0 - starProximity, 1.0);
}
</script>
<script type=application/glsl id=star-fragment-shader>
precision mediump float;
void main()
{
    gl_FragColor = vec4(1.0, 1.0, 1.0, 1.0);
}
</script>
<script type=application/glsl id=witch-vertex-shader>
uniform float time;
uniform vec2 scale;
uniform vec2 witchCenter;
uniform vec2 witchsize;
uniform vec2 witchField;
attribute vec2 position;
varying vec2 textureCoord;
void main()
{
    float effectiveTime = time;
    vec2 calculatedCenter = witchCenter - vec2(cos(time), sin(time)) * witchField;
    gl_Position = vec4(position * witchSize * scale + calculatedCenter * scale, 1.0, 1.0);
    textureCoord = vec2((1.0 + position.x) / 2.0, (1.0 - position.y) / 2.0);
}
</script>
<script type=application/glsl id=witch-fragment-shader>
precision mediump float;
uniform sampler2D witchTexture;
varying vec2 textureCoord;
void main()
{
    vec3 luminance = texture2D(witchtexture, textureCoord).rgb;
    gl_FragColor = vec4(luminance, luminance.x);
}
</script>
