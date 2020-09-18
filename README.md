# bundler-api

The app works as follows (note: front end not included in this api):

1) User types in the code editor

2) Code is sent to a backend API

3) The API runs babel and browserify (like webpack) on the code

4) The API returns a token identifying the bundled code

5) The client sticks that token into an Iframe. 

6) The iframe loads up the JS from the API server

7) Code gets executed!

Nice thing about this approach is that I can easily cache the bundled output. 
So if people keep executing the same code, I don't have to rebundle. 
In addition, since it uses babel and browserify (like webpack), you can write ES2015/16/17/etc code and it all correctly gets transpiled.
You will note that there are no import statements in the React code.  
They are optional - I parse the code, and if they are not added, any import statements (or a ReactDOM.render call) I automatically add that in.
