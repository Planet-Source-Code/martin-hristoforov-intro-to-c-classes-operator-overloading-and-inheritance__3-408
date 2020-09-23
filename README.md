<div align="center">

## Intro To C\+\+ classes, operator overloading and inheritance


</div>

### Description

This tutorial is supposed to teach you how to do classes, operator overloading, and inheritance.

NOTE: You need to have a good knowlege about structures.
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[Martin Hristoforov](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/martin-hristoforov.md)
**Level**          |Intermediate
**User Rating**    |3.8 (38 globes from 10 users)
**Compatibility**  |C\+\+ \(general\)
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/martin-hristoforov-intro-to-c-classes-operator-overloading-and-inheritance__3-408/archive/master.zip)





### Source Code

<p><b><h3> NOTE: Please put #include < iostream.h> at the beggining </b></h3></p>
<p>
If you're reading this then I guess that you want to learn some more about classes and some of the goodies that come with them.</p>
<p><b>NOTE:</b>This is a lenghty tutorial.<br><br>
Now first we are going to create a class. We'll call it OurClass because it is ours :). Here's the code:</p>
<p><b>class OurClass
<br>{
<br>private:				<i>	// optional but it is more readable that way </i>
<br>	int number1;
<br>public:				<i>	// not optional </i>
<br>	OurClass() : number1(0)<i>// Constructor
</i><br>{	}		<i>	// nothing in here but feel free to add whatever you want</i>
<br>	OurClass(int num): number1(num)<i>//Constructor with arguments</i>
<br>	{	}
<br>void set_number(int num)
<br>	{ number1 = num; }
<br>	int get_number()
<br>	{ return number1; }
<br>};	<i>// don't forget the ; at the end of every class</i>
</p></b>
<p>
This is our basic class from wich we are going to do everything else. You should notice the Constructor. This is a very usefull feuture because it lets you set the class variable(s) value(s) with it just like you would in a structure for instance. The constructor is basically an overloaded function so you should use it as you would overloaded functions. In our case if there are no arguments then number1 will be set to 0, and if an integer is passed then number1 will be set to the passed value. Lets see out how main goes:
</p>
<p><b>
int main()
<br>{
<br>	OurClass oc1;
<br>	OurClass oc2(10);
<br>	cout << oc1.getnumber() << endl << oc2.get_number(); <i>// returns 0 in the first line and </i>
						<i>	 // 10 on the next one</i>
<br>	oc1.set_number(100);
<br>	cout << endl << oc1.get_number();		<i>	 // shows 100</i>
<br>	return 0;
<br>}</p></b>
<p>
Easy eh? I tought so. See, using classes is esentially the same as using structures with the only difference being that you can have functions in them wich you use just like ordinary functions but with classname and a dot before the function name(you need to declare it first just like you would declare a structure.) You don't have access to the protected variable(s) in the class so it is essential to use class functions if you want to change any of those values. You can however declare the class variables as public instead of private but this is kind a pointless since one of the major ideas if classes is data hiding.
<br>Next thing we should do is overload an operator. Let's overload the ++ operator. All we gotta do is write one new functions in our class. The function code would be (this should be added inside the class):</p>
<p><b>OurClass operator ++ ()
<br> {
<br> ++count;
<br> OurClas temp;
<br> temp.count = count;
<br> return temp;
<br> }</p></b>
<p>
To see what happend let's make main looking like this:</p>
<p><b>
int main()
<br>{
<br>	OurClass oc1;
<br>	OurClass oc2(10);
<br>	cout << oc1.getnumber() << endl << oc2.get_number(); <i>// returns 0 in the first line and </i>
						<i>	 // 10 on the next one</i>
<br>	oc1.set_number(100);
<br>	cout << endl << oc1.get_number();	<i>	 // shows 100</i>
<br>	oc1++; cout << endl << oc1.getnumber();	 <i>	 // Now we get 101</i>
<br>	oc2 = oc1++ ; cout << endl << oc2.getnumber(); <i>	 // Getting 102</i>
<br>	return 0;
<br>}</b></p>
<p>
First off you need to use the operator keyword when overloading operators. In out case we don't need any arguments (the ++ and -- operators are the only ones that don't need arguments.) So when we say classname ++ we are basically calling the function ++ in classname and do what we need acordingly. <br>Now lets overload the + operator wich is a little bit harder. The code for the class will be (add it to the class): </p>
<p><b>OurClass operator + (OurClass second)
<br> {
<br> int answer = number1 + second.number1;
<br> return MyClass(answer);
<br> }</p></b>
<p><b><h5>Please note the return. Let me clarify, we are basically defining a new class, we put 10 in the parentless with wich we are calling the constructor so we return a class in wich the number1 integer is set to 10 (yes you can do this kind of stuff :).</p></b></h5>
<p>Main will look like:</p>
<b><p>
<br>int main()
<br>{
<br>	OurClass oc1;
<br>	OurClass oc2(10);
<br>	cout << oc1.getnumber() << endl << <br>oc2.get_number(); <i>// returns 0 in the first line and </i>
						<i>	 // 10 on the next one</i>
<br>	oc1.set_number(100);
<br>	cout << endl << oc1.get_number();	<i>		 // shows 100</i>
<br>	oc1++; cout << endl << oc1.getnumber();	 <i>	 // Now we get 101</i>
<br>	oc2 = oc1++ ; cout << endl << oc2.getnumber(); <i>	 // Getting 102</i>
<br>	OurClass oc3;
<br>	oc3 = oc1 + oc2; cout << endl << oc3.get_number;	 <i>// It should be 203</i>
<br>	return 0;
<br>}</p></b>
<p>Now you may ask what the hell happend? Well, it's actually pritty easy. Remeber when I told you that when you write classname ++ you are basically calling the ++ function in the classname. Well this is the same with the difference being that you say classname + classname2. So classname2 is the argument. See how easy it is? Read the note.</p>
<p><b><h4>NOTE:
classname - this is the class in wich the function + will be executed. The function name 		 can be +. -. *, /, <, >, % and all other operators (my guess will be that you could 	 even overload the AND(&&),OR(||) and NOT(!) ones.
classname2 - this is the class wich is sended as an so you would need to use classname2.</b></h4>
</p><p>
I hope you understood that one. You can overload operators for various things. For instance check out the string.h header and look at the code. You'll see one way to put it in a good use.
Next we are going to do some inheritance. So how do we do it? Well it is easy. First we will add 2 lines to our class, those lines will be( just after the the: </p>
<p><b>private:				<i><br>	// optional but it is more readable that way</i>
<br>	int number1;) :
<br>protected:
<br>	int pnumber;</p></b>
<p>So then we are going to make the derived class. We are going to call it Derived. Here is the code:</p>
<p><b>class Derived : public OurClass
<br>{
<br>private:
<br><i>	// you can put variables in here but we won't do that in this tutorial</i>
<br>public:
<br>	Derived(int num) : pnumber(num)
<br>	{	}
<br>	int get_derivednum()
<br>	{ return pnumber; }
<br>	void set_derivednum(int num)
<br>	{ pnumber = num; }
};</p></b>
<p>Let me try explain what the hell just happened. First of all we added the: </p>
<p><b>
protected:
<br> int pnumber; </p></b>
<p>
OurClass (wich we should now refer as our BaseClass.) Protected is essentially the same as private with the only difference being that you can access this variable from the derived class, where you cannot access the private variables. So the derived class is a class that inherits all the functions of the base class and you can also add new functions to the derived class(and variables). So for instance if we have a class that describe a human being we could put in it stuff like height, eye color, hair color, and all the feutures that are the same between a man and a woman. So then we could make 2 derived classes, one for a man and one for a woman and in it we could put only the characteristics that are special for each one(like genitals or something.) Anyway, lets see out main (I created a new main so you don&#8217;t get confused with all the previlious stuff).</p>
<p><b>
<br>Int main()
<br>{
	<br>Derived d1;
<br>d1.set_derivednum(145); cout << d1.get_derivednum() << endl; <i>// Those are the basic functions that are no different than the functions in the BaseClass </i>
<br>d1.set_number(10); cout << d1.get_number() << endl; <i>// Here we are using the //base class functions</i>
	return 0;
}</p></b>
<p>
So this outta make it quite clear. A derived class has all the so-called traits of the base class plus it&#8217;s own traits (traits are the functions and the variables). To use a variable from the base class when you&#8217;re in the derived class you need to get it as protected or as public. Declaring the derived class is made with:
Class DerivedClassName : public BaseClassName
This is how it&#8217;s done. If you don&#8217;t understand it then feel free to go and grab a book with a better explanation(I tried making this stuff as short as I could and if you get a book then you will read a lot more). So if you liked this tutorial send me an e-mail at mhrist@earthlink.net and I will try get more tutorials on the fascinating world of c++.</p>
Martin

