package com.impy.impyhw1_2ndtry;

import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;

import android.view.View;
import android.widget.Button;
import android.widget.TextView;

import java.util.Arrays;

public class MainActivity extends AppCompatActivity {

    Button num[], op[], lastButton;
    String token = "", operation = "";
    Integer res = null;
    TextView textView;


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        textView = (TextView)findViewById(R.id.textView);

        num = new Button[] {
                (Button)findViewById(R.id.b0),
                (Button)findViewById(R.id.b1),
                (Button)findViewById(R.id.b2),
                (Button)findViewById(R.id.b3),
                (Button)findViewById(R.id.b4),
                (Button)findViewById(R.id.b5),
                (Button)findViewById(R.id.b6),
                (Button)findViewById(R.id.b7),
                (Button)findViewById(R.id.b8),
                (Button)findViewById(R.id.b9),
        };
        op = new Button[] {
                (Button)findViewById(R.id.add),
                (Button)findViewById(R.id.sub),
                (Button)findViewById(R.id.mul),
                (Button)findViewById(R.id.div),
                (Button)findViewById(R.id.pow),
                (Button)findViewById(R.id.calc)
        };

        for (final Button button : num) {
            button.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    if (!Arrays.asList(num).contains(lastButton)) {
                        if (!token.equals("")) {
                            res = Integer.valueOf(token);
                        }
                        token = "";
                    }
                    token = token + button.getText();
                    textView.setText(token);
                    lastButton = button;
                }
            });
        }


        for (final Button button : op) {
            button.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View v) {
                    if (Arrays.asList(num).contains(lastButton) && !token.equals("")) {
                        Integer result = null;
                        switch (operation) {
                            case "add":
                                result = res + Integer.valueOf(token);
                                break;
                            case "sub":
                                result = res - Integer.valueOf(token);
                                break;
                            case "mul":
                                result  = res * Integer.valueOf(token);
                                break;
                            case "div":
                                result = res / Integer.valueOf(token);
                                break;
                            case "pow":
                                result = (int)Math.pow(res,Integer.valueOf(token));
                                break;
                        }
                        if (result != null) {
                            token = Integer.toString(result);
                            textView.setText(token);
                        }
                        res = result;
                        operation = getResources().getResourceEntryName(button.getId());
                        lastButton  = button;
                    }
                }
            });
        }

        ((Button)findViewById(R.id.clear)).setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                if (token.length() > 0) {
                    token = token.substring(0, token.length() - 1);
                    textView.setText(token);
                }
            }
        });

        if (savedInstanceState != null) {
            token = savedInstanceState.getString("token");
            operation = savedInstanceState.getString("operation");
            if (savedInstanceState.getInt("lastButton") != 0) {
                lastButton = (Button)findViewById(savedInstanceState.getInt("lastButton"));
            }
            res = savedInstanceState.getInt("res");
            textView.setText(token);
        }
    }

    @Override
    public void onSaveInstanceState(Bundle outState) {
        super.onSaveInstanceState(outState);
        outState.putString("token", token);
        outState.putString("operation", operation);
        if (lastButton != null) {
            outState.putInt("lastButton", lastButton.getId());
        }
        if (res != null) {
            outState.putInt("res", res);
        }
    }
}
