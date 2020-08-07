<template>
  <div id="students">
  

     
    <table>
      <thead>
        <tr>
            <th>Lesson Code</th>
            <th>First Grade</th>
            <th>Two Grade</th>
            <th>Final Grade</th>
            <th>Grade Status</th>
            <th>Warnings</th>
            <th>Delete</th>
        </tr>
</thead>
        <tr v-for="(student,index) in students" :key="student.index">
            <td> <input type="text" v-model="student.code"></td>
            <td><input type="number" v-model="student.firstgrade"></td>
            <td> <input type="number" v-model="student.twograde"></td>
            <td> <input type="number" v-model="student.finalgrade"></td>
            <td>{{ComputGrad(student)}}</td>
            <td v-bind:class="{failed:ComputGrad(student)<60, passed:ComputGrad(student)>=60}">{{ComputGrad(student)>=60 ? 'Passed':'Failed'}} </td>
            <td><button @click="deletlesson(index)"><em>&times;</em></button></td>
        </tr>

    </table><br>
  <div>
   <button class="button" @click="addlesson">Add</button>
   <br>
   <h3>Avarage:{{computedavarage}}</h3>
     </div>
    
  </div>
  
</template>

<script>
export default {
  props:{
    students:{
      type:Array,
      required:true
    },
   
  },
 
  
  data () {
    return {
     
    }
  },
  methods:{
    ComputGrad:function(students){
      var total=0;
      total=((students.firstgrade * .30)+(students.twograde * .30)+(students.finalgrade * .40));
      return total.toFixed(2);
    },
    addlesson:function(){
      this.students.push({
        code:"",
        firstgrade:'',
        twograde:'',
        finalgrade:''
      });
    },
    deletlesson:function(index){
      this.students.splice(index,1);
     
    }


  },
   computed:{
     computedavarage:function(){
       var avar=0;
       for(var i=0;i<this.students.length;i++){
         avar += this.ComputGrad(this.students[i]);
       
         return (avar / this.students.length).toFixed(2);

       }
      
     }
   },


   
    
 }
//   beforeCreate(){
//     alert('beforcreate');
//   },
//   updated(){
// alert("update");
//   },
//   beforeUpdate(){
//     alert("beforeupdate");
//   },
//   created(){
//     alert("created")
//   },
//   mounted(){
//     alert("mounted")
//   },
//   beforeMount(){
//     alert("before mounted")
//   }

</script>
<style scoped>

table {
	border: 1px solid rgb(126, 117, 117);
	border-collapse: collapse;
	border-spacing: 0;
	width: 100%;
}
	thead td {
		background-color: #E1E7EE;
	}
	th,
	td {
		border-bottom: 1px solid #ccc;
		line-height: 1.2;
		text-align: center;
		padding: 0.5rem;
    font-weight: bold;
    
	}
	th {
		background: #F5F7Fb;
		font-size: 0.8em;
		letter-spacing: 1px;
		text-transform: uppercase;
    font-weight:700;
	}

input[type=text],
input[type=number] {
	width: 100%;
	padding: 0.5rem;
  font-weight: bold;
}

input[type=submit],



.actions {
	text-align: right;
	white-space: nowrap;
	width: 20px * 4;
}
.failed{
  background:orangered;
}
.passed{
  background:greenyellow;
}
.box {
	margin-top: 1em;
	padding: 1em;
	background: #eee;
}

textarea {
	font-family: monospace;
	font-size: 12px;
	margin: 0.5em 0 0 0;
	padding: 0.5em;
	width: 100%;
}

.hidden {
	display: none;
}
.button {
  background-color: yellowgreen; /* Green */
  border: 1px solid black;
  color: black;
  padding: 12px 24px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 14px;
  font-weight: bold;
  margin: 4px 2px;
  transition-duration: 0.4s;
  cursor: pointer;
}
.button:hover{
  background-color:mediumspringgreen;
  color:black
}
em{
  
  color:red;
  font-size:20px;
  font-weight: bolder;
  
  
}

</style>