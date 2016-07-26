##View Basic

We can generally assume that each view is a unit on our interface, such as a button, a text window. I personally suggest we initialize and modify views through Java code, especially those views that will constantly change in response to user behaviors.


When you wanna modify a view in Java, you have to get it from res file
```
// In activity
TextView prediction = (TextView) findViewById(R.id.prediction_text);
         prediction.setText("");
         
// If not in activity, get activity first
TextView prediction = (TextView) getActivity().findViewById(R.id.prediction_text);
```

To intialize an image button, we could:
```
private ImageButton buttonPrediction;
buttonPrediction = (ImageButton) findViewById(R.id.procare_button_prediction);
buttonPrediction.setOnClickListener(this);
((ImageButton) buttonPrediction).setImageResource(R.drawable.monitor);
buttonPrediction.setScaleType(ImageView.ScaleType.FIT_CENTER);
```
