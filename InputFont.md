
Go to directory app>src>main, create a folder named "assets", inside which create another folder "fonts". Put your font file here, and implement the following code in your program: 

```
Typeface customFont = Typeface.createFromAsset(getAssets(), "fonts/Roboto-Light.ttf");
mEmailView = (AutoCompleteTextView) findViewById(R.id.sign_in_email_input);
mEmailView.setTypeface(customFont);
```

This change only the user input font, not the hint font.


(http://stackoverflow.com/questions/27588965/how-to-use-custom-font-in-android-studio)
