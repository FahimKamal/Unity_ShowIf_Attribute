# Unity_ShowIf_Attribute
ShowIf Attribute is a small script that will help you to hide or disable a SerializeField in inspector in Unity editor. Just download the script and add it in your project.

I have taken this solution from a StackOverFlow answer. The link to the question is: 
[here](https://stackoverflow.com/questions/58441744/how-to-enable-disable-a-list-in-unity-inspector-using-a-bool "How to enable/disable a List in Unity inspector using a bool?")

## Usage
+ Using a field to hide/show another field:

```c#
public bool showHideList = false; 
[ShowIf(ActionOnConditionFail.DontDraw, ConditionOperator.And, nameof(showHideList))]
public string aField = "item 1";
```
![hide/show a field](https://gyazo.com/7aa9ecb607415d71bf5c5948f856eab1.gif "Hide/show a field")

+ Using a field to enable/disable another field:

```c#
public bool enableDisableList = false;

[ShowIf(ActionOnConditionFail.JustDisable, ConditionOperator.And, 
nameof(enableDisableList))]
public string anotherField = "item 2";
```
![Enable/Disable a field](https://gyazo.com/f94d76702f32adf4d6a22eccaf5a0d4a.gif "enable/disable a field")

+ Using multiple conditions on the same field:

```c#
public bool condition1;    
public bool condition2;    
[ShowIf(ActionOnConditionFail.JustDisable, ConditionOperator.And, nameof(condition1), 
nameof(condition2))]    
public string oneLastField= "last field";
```
![hide/show a field](https://gyazo.com/832b043e065741a170f9a5cbc42abe10.gif "Use multiple conditions on a same field")

+ Using a method to get a condition value:

```c#
[ShowIf(ActionOnConditionFail.JustDisable, ConditionOperator.And,nameof(CalculateIsEnabled))]
public string yetAnotherField = "one more";    
public bool CalculateIsEnabled()    
{
    return true;    
}
```
![Using a method to get a condition value](https://gyazo.com/f87aae44ff47e046b5f3dc5b3e26c8f9.gif "Using a method to get a condition value")
