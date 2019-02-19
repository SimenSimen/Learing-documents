### 接口說明

1. 再函式內部使用物件時可以捕獲引用不存在屬性的錯誤
2. 可以對屬性進行預先的定義

一般用法

```ts

interface Person
{
    name: string,
    age: number,
}

function printPerson(personObj : Person)
{
    console.log(`I got a person, name: ${personObj.name} age: ${personObj.age} years old`);
}

let simen = {name: 'simen' , age: 17};

printPerson(simen);

```

可選屬性

```ts

interface Person
{
    name: string,
    age: number,
    height?: number //可選屬性
}

function printPerson(personObj : Person)
{
    console.log(`I got a person, name: ${personObj.name} age: ${personObj.age} years old`);
    if (personObj.height)
        console.log('too tall')
}

let simen = {name: 'simen' , age: 17};

printPerson(simen);

```

只讀屬性

```ts

interface Person
{
    readonly name: string,
    readonly age: number,
}

let simen = {name: 'simen' , age: 17};
simen.age = 10; //Error

```

只讀屬性 Array

```ts

let a : number[] = [1,2,3,4];
let ro : ReadonlyArray<number> = a;

ro[0] = 12; //Error
ro.push(5); // error!
ro.length = 100; // error!
a = ro; // error!

```

函式類型

```ts
interface SearchFunc {
    (source: string, subString: string): boolean;
}

let mySearch: SearchFunc;
mySearch = function(src: string, sub: string): boolean {
    let result = src.search(sub);
    return result > -1;
}


```

可索引的類型
```ts
    interface StringArray {
        [index: number]: string;
    }

    let myArray: StringArray;
    myArray = ["Bob", "Fred"];

    let myStr: string = myArray[0];
```