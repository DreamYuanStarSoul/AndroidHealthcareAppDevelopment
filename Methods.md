

##UserLoginTask
```
public class UserLoginTask extends AsyncTask<Void, Void, Boolean> {}

private UserLoginTask mAuthTask = null;
mAuthTask = new UserLoginTask(email, password); // The verification process
mAuthTask.execute((Void) null); // What happen next: jump to another page, hint an error, or close the program
```
execute() include four stages of methods, onPreExecute(),doInBackground(Params...), onProgressUpdate(Progress...), and onPostExecute(Result). Usually, we need to override at least doInBackground(), and in most cases onPostExecute()
(https://developer.android.com/reference/android/os/AsyncTask.html)
