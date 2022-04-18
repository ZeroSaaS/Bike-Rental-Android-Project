package com.example.greg.gregsbicyclerentals;
import android.app.DatePickerDialog;
import android.app.Dialog;
import android.app.DialogFragment;
import android.app.TimePickerDialog;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.DatePicker;
import android.widget.TextView;
import android.widget.TimePicker;
import android.widget.Toast;
import java.text.DateFormat;
import java.text.SimpleDateFormat;
import java.util.Calendar;

public class MainActivity extends AppCompatActivity {
    //Module level declarations that will be used in multiple methods
    TextView m_tvReservation;
    //Get the calendar format for the device this is running on
    Calendar m_timeReservations = Calendar.getInstance();
    Calendar m_calReservations = Calendar.getInstance();
    DateFormat m_dfDate = DateFormat.getDateInstance();
    DateFormat m_dfTime = DateFormat.getTimeInstance();
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        //declare local variables to access GUI components/widgets
        m_tvReservation = (TextView) findViewById(R.id.txtReservation);
        Button btnDateLogic = (Button) findViewById(R.id.btnDate);
        //Button btnTimeLogic = (Button) findViewById(R.id.btnTime);
        //declare and click code logic for btnDateLogic
        btnDateLogic.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                //display DatePickerDialog showing today as the default
                //and link the DatePickerDialog to the listener that
                //will process when the user selects a date
                new DatePickerDialog(MainActivity.this,
                        dpListener,
                        m_calReservations.get(Calendar.YEAR),
                        m_calReservations.get(Calendar.MONTH),
                        m_calReservations.get(Calendar.DAY_OF_MONTH)).show();
            }
        });
    }
    //DatePickerDialog Listener logic that is called when the user selects a date
    DatePickerDialog.OnDateSetListener dpListener = new DatePickerDialog.OnDateSetListener() {
        public void onDateSet(DatePicker view, int iYear, int iMonthOfYear, int iDayOfMonth) {
            //get todays date
            Calendar calToday = Calendar.getInstance();
            SimpleDateFormat sdf = new SimpleDateFormat("dd-MM-yyyy");
            //set the module calendar object to what the user selected
            m_calReservations.set(Calendar.YEAR, iYear);
            m_calReservations.set(Calendar.MONTH, iMonthOfYear);
            m_calReservations.set(Calendar.DAY_OF_MONTH, iDayOfMonth);
            //compare the selected date to todays date, if it is less you cannot reserve before today
            if ((sdf.format(m_calReservations.getTime()).compareTo(sdf.format(calToday.getTime()))) < 0) {
                m_tvReservation.setText("");
                Toast.makeText(MainActivity.this, "Reservation date must be today or after.", Toast.LENGTH_LONG).show();
            } else {
                //show the user the selected date
                m_tvReservation.setText("Your Reservation is set for: " + m_dfDate.format(m_calReservations.getTime()));
            }
        }
  };
//Multiple Issues running this code below - decided to exclude it so the application would compile.
/*
    Button btnTimeLogic = (Button) findViewById(R.id.btnTime);
    btnTimeLogic.setOnClickListener(new View.OnClickListener()
    {
        public void onClick (View v){
        new TimePickerDialog(MainActivity.this,
                tpListener,
                m_timeReservations.get(Calendar.HOUR_OF_DAY),
                m_timeReservations.get(Calendar.MINUTE)).show();
    }
    }
            //TimePickerDialog Listener logic that is called when the user selects a date
            TimePickerDialog.OnTimeSetListener tpListener = new TimePickerDialog.OnTimeSetListener() {
                public void onTimeSet(TimePicker view, int iHour, int iMinute) {
                    SimpleDateFormat sdfTime = new SimpleDateFormat("hh:mm");
                    Calendar calTime = Calendar.getInstance();
                    //set the module calendar object to what the user selected
                    m_timeReservations.set(Calendar.HOUR_OF_DAY, iHour);
                    m_timeReservations.set(Calendar.MINUTE, iMinute);
                    //show the user the selected time
                    m_tvReservation.append(" at " + m_dfTime.format(m_timeReservations.getTime()));
                }
            };
            };
*/
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.menu_main, menu);
        return true;
    }
    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        // Handle action bar item clicks here. The action bar will
        // automatically handle clicks on the Home/Up button, so long
        // as you specify a parent activity in AndroidManifest.xml.
        int id = item.getItemId();
        //noinspection SimplifiableIfStatement
        if (id == R.id.action_settings) {
            return true;
        }
        return super.onOptionsItemSelected(item);
    }
}
