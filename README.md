# adapter-Android
Adapter in android 

#Code 

```
package com.example.adaptor

import android.content.Context
import android.os.Build.VERSION_CODES.R
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.speech.tts.TextToSpeech
import android.view.LayoutInflater
import android.view.View
import android.view.ViewGroup
import android.widget.AdapterView
import android.widget.ArrayAdapter
import android.widget.ImageView
import android.widget.ListView
import android.widget.TextView

class MainActivity : AppCompatActivity() {

    data class Personality(val dp : Int, val name : String, val dob : String)


    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        val data = arrayOf(
            Personality(R.drawable.edhi, "Mr Edhi Sahab", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940"),
            Personality(R.drawable.edhi, "Abdul Sattar Edhi", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940"),
            Personality(R.drawable.edhi, "Abdul Sattar Edhi", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940"),
            Personality(R.drawable.edhi, "Abdul Sattar Edhi", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940"),
            Personality(R.drawable.edhi, "Abdul Sattar Edhi", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940"),
            Personality(R.drawable.edhi, "Abdul Sattar Edhi", "1/1/1920"),
            Personality(R.drawable.quaid, "Quaid e Azam", "25/12/1876"),
            Personality(R.drawable.nas, "Allam Iqbal", "1/1/1877"),
            Personality(R.drawable.nas, "Nisar Ahmed Siddiqui", "1/1/1940")
        )
        val adapter = PersonalityAdapter(this, R.layout.row, data)

        val tts:TextToSpeech= TextToSpeech(this,TextToSpeech.OnInitListener {


        })
        //val adapter = ArrayAdapter(this,android.R.layout.simple_list_item_1,data)
        val ListtView: ListView =findViewById(R.id.listview)
        ListtView.adapter=adapter
        ListtView.setOnItemClickListener(AdapterView.OnItemClickListener { adapterView, view, i, l ->
        tts.speak(data[i].name, TextToSpeech.QUEUE_ADD,null,"231")


        })

    }


    class PersonalityAdapter(context: Context, resource: Int, objects: Array<out Personality>) :
        ArrayAdapter<Personality>(context, resource, objects) {

        val cont = context
        val res = resource
        val data = objects

        override fun getView(position: Int, convertView: View?, parent: ViewGroup): View {
            val view  = LayoutInflater.from(context).inflate(res, parent, false)

            val dp : ImageView = view.findViewById(R.id.dp)
            dp.setImageResource(data[position].dp)

            val name : TextView = view!!.findViewById(R.id.name)
            name.text = data[position].name

            val dob : TextView = view.findViewById(R.id.dob)
            dob.text = data[position].dob

            return view;
        }

    }
}

```


# Ui 

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="horizontal"
    tools:context=".MainActivity">


    <ListView
        android:id="@+id/listview"
        android:layout_width="420dp"
        android:layout_height="733dp"
        app:layout_constraintBottom_toBottomOf="parent"
        tools:layout_editor_absoluteX="0dp" />

</LinearLayout>
```
