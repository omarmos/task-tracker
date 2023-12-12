# task-traker

Each vue app has 3 sections
1- <template>Output to html (id = #app)

</template>

2- <script>
java script logic of the page
when you want to imuse a component you import it here and export it in the comonenet object
eg:
import HelloWorld from './components/HelloWorld.vue'

export default {
name: 'App',
components: { //components object
HelloWorld
}
}
</script>

3- <style>
page styling - <style scoped> scoped means style only applied to this componented
</style>

##################################################################

Props
In Vue, props are custom attributes that you can register on any component.
You define your data on the parent component and give it a value. Then, you go to the child component
that needs that data and pass the value to a prop attribute.
Therefore, the data becomes a property in the child component.

defining prop in helloworld component(parent here) and passing it to app comonent (child here)

in HelloWorld component:

 <script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

using prop in app.vue component:

<HelloWorld msg="Welcome to Your Vue.js App"/>

props can be defined as an array or object
as an array props: ['title']
or object props:{title: String} // title hna bnkot string 3shan to be constrctor

for e.g fe al color ma bngol props:{ color:green } wrong to be re used bngol color:string o ba3adak we assaing the value green fe al instanse.

to assain text 3ade we use {{}} bs to assagin colors(styles) or images we use v-bind: or :

##################################################################
Events:
v-on: click='onClick()' shortcut @click then u define a method for onClick()
<button @click="onClick()" :style="{background:color}" class="btn" > {{ text }}</button>

methods: {
onClick(){
console.log("clicked")
}

created(): is a lifecycle method we use to load data when component is rendered

for now we going to set our data in a top level component which is (app comonent ) so we access it for any componenet
to dod that we are going to define data() which is an faunction that return data object
data(){
return{
tasks:[]
}
}

now we want to load the data into tasks via created
data(){
return{
tasks:[]
}
}

created(){
this.tasks = [
{
"id": "1",
"text": "Doctors Appointment",
"day": "March 5th at 2:30pm",
"reminder": true
},
{
"id": "2",
"text": "Meeting with boss",
"day": "March 6th at 1:30pm",
"reminder": true

        },
        {
      "id": "3",
      "text": "Food shopping",
      "day": "March 7th at 2:00pm",
      "reminder": false
        }
    ]

}

now we create a task component to pass tis data into when we render the component.

v-bind is used to get imges, objects arrays basiclay any prop other than text

tasks component
/_ eslint-disable _/
<template>

<div  :key="task.id" v-for="task in tasks" >
<h3>{{ task.text }}</h3>
</div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: 'Tasks',
  props: {
    tasks: Array
  },


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

in app component we call tasks and pass the array as props via v-bind
<Tasks :tasks="tasks" />
remeber we defined the data in App not tasks because it's a top level component that can be accessed by any othe component
and yes we can simply delete the prop from tasks and pass the data into it bta3 al tut da b7b y3gd bs
simply
/_ eslint-disable _/
<template>

<div  :key="task.id" v-for="task in tasks" >
<h3>{{ task.text }}</h3>
</div>
</template>

<script>
export default {
  // eslint-disable-next-line
  name: 'Tasks',

  data(){
  return{
    tasks:[]
  }
},

  created(){

      this.tasks =[
     {
    "id": "1",
    "text": "Doctors Appointment",
    "day": "March 5th at 2:30pm",
    "reminder": true
    },
    {
    "id": "2",
    "text": "Meeting with boss",
    "day": "March 6th at 1:30pm",
    "reminder": true
    },
    {
   "id": "3",
   "text": "Food shopping",
   "day": "March 7th at 2:00pm",
   "reminder": false
        }

      ]
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

further we wanna break the tasks to a single task component
so we create a task component and pas task.text as a prop

to include any cdn place it in public index.html like font awesome ..etc

##################################################################
if statment:
if the reminder is se to true we want to have green bar on it if not no green bar
so in task class we set the if statmen
from <div class= 'task'>
to <div :class = '[task.reminder ? 'reminder' : '' , 'task']'

that could be red like if the task.reminder is set to true (before the ?) then place reminder class if not then place ('') no reminder class and then add ,'task' class in both cases
before ? is the condition
after ? if it's true do this 'reminder'
: two dots if it's flase means else
the colom , 'task' is to add another class
and since we are passing two classes as objects in an array we have to use v-bind on the class to become :class=
###################################################################

Emit
we use emit function to pass data from child component to higher parent component (catch it in the higher component)
so if we want to delete task from the task component we emit to tasks components and teen emit to app component where data is and can be handeled via filter
####################################################################

jsonserver is like a fake server that simulates backend , where we get data from
now we are going to store the data (tasks) in db.json and fetch it rather than hard code it like we did above
