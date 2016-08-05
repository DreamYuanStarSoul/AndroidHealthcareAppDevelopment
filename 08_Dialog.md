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


## As a fragment
```
public class FragmentBasicInfo extends DialogFragment {

    /** creates a new instance of PropDialogFragment */
    public static FragmentBasicInfo newInstance() {
        return new FragmentBasicInfo();
    }

    @Override
    public Dialog onCreateDialog(Bundle savedInstanceState) {

        LayoutInflater inflater = getActivity().getLayoutInflater();
        View view = inflater.inflate(R.layout.fragment_basic_info, null);

        // Use the Builder class for convenient dialog construction
        AlertDialog.Builder builder = new AlertDialog.Builder(getActivity());
        builder.setView(view)
                .setPositiveButton(getResources().getString(R.string.choice_confirm), new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int id) {
                        // Change information in the database
                        // ...
                        dialog.cancel();
                    }
                })
                .setNegativeButton(getResources().getString(R.string.choice_cancel), new DialogInterface.OnClickListener() {
                    @Override
                    public void onClick(DialogInterface dialog, int id) {
                        dialog.cancel();
                    }
                });

        // Create the AlertDialog object and return it
        return builder.create();
    }
}
```
```
    private void show() {
        // Initialize resources and clear data
        FragmentBasicInfo fragmentBasicInfo;

        FragmentManager fragmentManager = getFragmentManager();
        FragmentTransaction transaction = fragmentManager.beginTransaction();
        DialogFragment temp = FragmentBasicInfo.newInstance();
        temp.show(transaction, "basic_info");

    }
```
(http://stackoverflow.com/questions/13257038/custom-layout-for-dialogfragment-oncreateview-vs-oncreatedialog)

