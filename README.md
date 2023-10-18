package com.example.spiner;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.Spinner;
import android.widget.TextView;
import android.widget.Toast;

public class MainActivity extends AppCompatActivity {

    EditText et1;
    TextView tv1;
    Spinner sp1;
    CheckBox chk1, chk2, chk3, chk4;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        et1 = (EditText)findViewById(R.id.etnNumero1);
        tv1 = (TextView)findViewById(R.id.txtvResultado);
        sp1 = (Spinner)findViewById(R.id.spnNum1);
        String [] Spiner ={"mm", "dm", "cm", "m", "dam", "nm", "km"};
        ArrayAdapter<String> AdaptadorDeLista = new
        ArrayAdapter<String>(this, android.R.layout.simple_spinner_item, Spiner);
        sp1.setAdapter(AdaptadorDeLista);
    }
    public void Actualizar(View Vista)
    {
        String ValorCadena1 = et1.getText().toString();
        double ValorEntero1 = Double.parseDouble(ValorCadena1);
        String EleccionDeLista = sp1.getSelectedItem().toString();
        double ResultadoEntero;
        String ResultadoCadena = "";
        switch (EleccionDeLista)
        {
            case "mm":
                ResultadoEntero = ValorEntero1 * 1000;
                ResultadoCadena =  String.valueOf(ResultadoEntero);
                break;

            case "dm":
                ResultadoEntero = ValorEntero1 * 100;
                ResultadoCadena = String.valueOf(ResultadoEntero);
                break;

            case "cm":
                ResultadoEntero = ValorEntero1 * 10;
                ResultadoCadena =  String.valueOf(ResultadoEntero);
                break;

            case "m":
                ResultadoEntero = ValorEntero1 * 1;
                ResultadoCadena = String.valueOf(ResultadoEntero);
                break;

            case "dam":
                ResultadoEntero = ValorEntero1 /10;
                ResultadoCadena =  String.valueOf(ResultadoEntero);
                break;

            case "nm":
                ResultadoEntero = ValorEntero1 /100;
                ResultadoCadena = String.valueOf(ResultadoEntero);
                break;

            case "km":
                ResultadoEntero = ValorEntero1 /1000;
                ResultadoCadena =  String.valueOf(ResultadoEntero);
                break;
        }

        tv1.setText(ResultadoCadena + "");
    }
}
