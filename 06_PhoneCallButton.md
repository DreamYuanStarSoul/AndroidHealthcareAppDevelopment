
Use "ACTION_DIAL" to call for the dial panel, use "ACTION_CALL" to call directly, which needs additional permission
```
emergentCallButton =  (Button) findViewById(R.id.homepage_button_emergent_call);
        emergentCallButton.setOnClickListener(new View.OnClickListener() {
          @Override
          public void onClick(View view) {
              Intent callIntent = new Intent(Intent.ACTION_DIAL);
                     callIntent.setData(Uri.parse("tel:119"));
              if (callIntent.resolveActivity(getPackageManager()) != null) {
                  startActivity(callIntent);
              }

          }
      });
```

Add permission in Menifast
```
<uses-permission android:name="android.permission.CALL_PHONE"></uses-permission>
```
