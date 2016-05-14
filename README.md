# UnityEnumEditor
Unity editor extension for enums

Example : 

```C#
    // A Flags enum
    [Flags]
    public enum AnimalType {
        None = 0,
        Cat = 1,
        Cow = 2,
        Dog = 4,
        Fish = 8,
        Racoon = 16
    }

    public class EnumEditorExample : MonoBehaviour {
        // Use attribute EnumFlags to enable EnumEditor
        [EnumFlags]
        public AnimalType Animal;

        void Start() {
            // A helper extension is provided to check for flags
            if (Animal.HasFlag(AnimalType.Cat)) {
                Debug.Log("Cat flag is set");
            }

            if (Animal.HasFlag(AnimalType.Cat | AnimalType.Fish)) {
                Debug.Log("Cat & Fish flags are set");
            }
        }
    }
```

To use it in your own custom inspectors, this is the way :

```C#
  var mySerializedObject = new SerializedObject(MyObject);
  // GUIContent.none removes the text in front of the enum line
  EditorGUILayout.PropertyField(mySerlializedObject.FindProperty("MyEnumName") /*, GUIContent.none */);
```
