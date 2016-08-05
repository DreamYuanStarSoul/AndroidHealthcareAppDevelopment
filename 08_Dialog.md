## As a method
```
    // Invoke this method to make emergent contact
    public void emergentCallDialog(View view) {
        AlertDialog.Builder alertDialogBuilder = new AlertDialog.Builder(this);
        alertDialogBuilder.setMessage("Are you sure to make this call?");

        alertDialogBuilder.setPositiveButton(getResources().getString(R.string.choice_yes), new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int id) {
                // Send out the signal to our verification process or service center
                // ...
                dialog.cancel();
            }
        });

        alertDialogBuilder.setNegativeButton(getResources().getString(R.string.choice_no), new DialogInterface.OnClickListener() {
            @Override
            public void onClick(DialogInterface dialog, int id) {
                dialog.cancel();
            }
        });

        AlertDialog alertDialog = alertDialogBuilder.create();
        alertDialog.show();
    }
```
