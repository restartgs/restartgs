// MainActivity.java
package com.restartgs;

import android.content.Intent;
import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;
import android.view.View;
import android.widget.Button;

public class MainActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        
        Button serviceButton = findViewById(R.id.btnService);
        Button inventoryButton = findViewById(R.id.btnInventory);

        serviceButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this, ServiceActivity.class));
            }
        });

        inventoryButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                startActivity(new Intent(MainActivity.this, InventoryActivity.class));
            }
        });
    }
}

// ServiceActivity.java
package com.restartgs;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class ServiceActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_service);
    }
}

// InventoryActivity.java
package com.restartgs;

import android.os.Bundle;
import androidx.appcompat.app.AppCompatActivity;

public class InventoryActivity extends AppCompatActivity {
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_inventory);
    }
}

// FirebaseService.java
package com.restartgs;

import com.google.firebase.firestore.FirebaseFirestore;
import java.util.Map;

public class FirebaseService {
    private final FirebaseFirestore db = FirebaseFirestore.getInstance();

    public void addService(String collection, Map<String, Object> data) {
        db.collection(collection).add(data);
    }
}
