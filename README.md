# AndroidAppTrial
Share some problems that I have encountered, hopefully you will find what you're looking for here.


Question:
Shouldn't "final Boolean success" be false as default? Why success is true...
```
        protected void onPostExecute(final Boolean success) {
            mAuthTask = null;
            showProgress(false);

            if (success) { // Finish login and start homepage
                finish();
                Intent intent = new Intent(LoginActivity.this, MyActivity.class);
                startActivity(intent);

            } else {
                mPasswordView.setError(getString(R.string.error_incorrect_password));
                mPasswordView.requestFocus();
            }
        }
```
