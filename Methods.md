

##UserLoginTask
```
public class UserLoginTask extends AsyncTask<Void, Void, Boolean> {}

private UserLoginTask mAuthTask = null;
mAuthTask = new UserLoginTask(email, password);
mAuthTask.execute((Void) null);
```
execute() include four stages of methods, onPreExecute(),doInBackground(Params...), onProgressUpdate(Progress...), and onPostExecute(Result). Usually, we need to override at least doInBackground(), and in most cases onPostExecute()
(https://developer.android.com/reference/android/os/AsyncTask.html)
