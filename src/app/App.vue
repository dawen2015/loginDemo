<template>
    <div class="jumbotron">
        <div class="container">
            <div class="row">
                <div class="col-sm-6 offset-sm-3">
                    <router-view></router-view>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'app'
};
</script>

<style>
#app {
  text-align: center;
  margin-top: 60px;
}

html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
  margin: 0;
	padding: 0;
	border: 0;
	font-size: 14px;
	vertical-align: baseline;
    line-height: 14px;;
    font-family:Roboto;
}

body {
    margin: 0;
    background-color: #F0F0F0;
    }
    h1 {
        padding: 0;
        margin-top: 0;
    }
    #app {
        width:100%;
        margin: auto;
    }

/* Style the input container */
.input-container {
  display: flex;
  width: 100%;
  margin-bottom: 1.07rem;
  border-radius: 0 !important;
}

/* Style the form icons */
.icon {
  padding: 0.71rem;
  background: #ffffff;
  color: #000000;
  min-width: 4rem;
  text-align: center;
  margin: 0;
  font-size: 1.28rem;
}

/* Style the input fields */
.input-field {
  width: 100%;
  padding: 0.71rem;
  outline: none;
  border-width: 0px;
  padding-left: 0;
  width: 100%;
  border-radius: 0 !important;
}

.input-field:focus {
  border-width: 0px;
  background: #ffffff;
}

.invalid-feedback{
  padding:0.5rem;
}

h2 { 
font-family: Rift;
font-style: normal;
font-weight: normal;
font-size: 3rem;
line-height: 3.57rem;
text-align: center;
letter-spacing: 0.08rem;
text-transform: uppercase;
color: #4D008C;
}

h3 {
  text-transform: uppercase;
  font-size: 2.86rem;
  font-family: Rift;
  color: #ffffff;
}

</style>
