# SimpleAdapter

[![N|Solid](https://img.shields.io/badge/Android%20Arsenal-Simpler%20Recycler%20View%20Adapter-brightgreen.svg)](https://android-arsenal.com/details/1/5354)

SimpleAdapter used to simplfy the adapter structure for RecyclerView with databinding
  - Easy to use.
  - No need to create adapter (Seperate java files).
  - Use of databinding.

### Download
Include the following dependency in your apps build.gradle file.
```
compile 'com.master.android:simpleadapter:2.0'
```

### How to use
#### Java
```java
final ArrayList<User> list = new ArrayList<>();        
list.add(new User("Pankaj"));
list.add(new User("Sumit"));

RecyclerView recyclerView = (RecyclerView) findViewById(R.id.recyclerView);
recyclerView.setLayoutManager(new LinearLayoutManager(this));
recyclerView.setAdapter(SimpleAdapter.with(R.layout.item, list, new SimpleAdapter.Binder<User, ItemBinding>() {
    @Override
    public void onBind(int position, User model, ItemBinding binding) {
        binding.text.setText(model.name);
    }
}));

// Using SmartBinder
recyclerView.setAdapter(SimpleAdapter.with(R.layout.item, list, new SimpleAdapter.SmartBinder<User, ItemBinding>() {
    @Override
    public void onBind(int position, User model, ItemBinding binding) {
        binding.text.setText(model.name);
    }

    @Override
    public void onClick(View view, User model, int position) {
        super.onClick(view, model, position);
    }

    @Override
    public void onCheckedChange(View view, User model, int position) {
        super.onCheckedChange(view, model, position);
    }
}).setClickableViews(R.id.text).setCheckableView(R.id.checkbox));
```

#### Kotlin
```kotlin
val list = ArrayList<User>()
        
list.add(User("Pankaj"))
list.add(User("Sumit"))

val recyclerView = findViewById<RecyclerView>(R.id.recyclerView)
recyclerView.layoutManager = LinearLayoutManager(this@MyActivity)
recyclerView.adapter = with(R.layout.item, list, { position: Int, model: User, binding: ItemBinding ->
    binding.text.setText(model.name)
})

// Using SmartBinder
recyclerView.adapter = with(R.layout.item, list, object : SimpleAdapter.SmartBinder<User, ItemBinding>() {
    override fun onBind(position: Int, model: User, binding: ItemBinding) {
        binding.text.setText(model.name)
    }

    override fun onClick(view: View?, model: User?, position: Int) {
        super.onClick(view, model, position)
    }

    override fun onCheckedChange(view: View?, model: User?, position: Int) {
        super.onCheckedChange(view, model, position)
    }
}).setClickableViews(R.id.text).setCheckableView(R.id.checkbox)
```

### License
```
Copyright 2017 Pankaj Sharma

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
