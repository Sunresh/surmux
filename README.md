# Shared preference save
1.
compile 'com.pixplicity.easyprefs:library:1.9.0'
2.
android:name=".MyApplication"
3.

public class MyApplication extends Application {

    @Override
    public void onCreate() {
        super.onCreate();
        // Initialize the Prefs class
        new Prefs.Builder()
			.setContext(this)
			.setMode(ContextWrapper.MODE_PRIVATE)
			.setPrefsName(getPackageName())
			.setUseDefaultSharedPreference(true)
			.build();
    }
}


4.

public class MainActivity extends Activity {
	private Set<String> value=null;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        Prefs.putString("SAVED_TEXT", "text");
		Set<String> v= new HashSet<String>();
		v.add("rr");v.add("rur");
		v.add("rru");v.add("ror");
		
		Prefs.putStringSet("KEY_ARRAY",v);
		
		
		Set<String> data = Prefs.getStringSet("KEY_ARRAY", value);
		TextView tt= (TextView)findViewById(R.id.activitymainTextView1);
		String s= data.toString();
		tt.setText(s);
    }
}



