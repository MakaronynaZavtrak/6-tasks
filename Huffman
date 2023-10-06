let str = "abrakadabra"//входная строка
const primalLen = str.length
let arr = []
//TODO: sorting
console.log("Input string: ", str)

for (let i = 0; i < str.length; i++){//Создаем массив уникальных символов с частотами
    if (str[i] in arr){
        arr[str[i]]++
    } else {
    arr[str[i]]=1
    }
}




let count = 0
let objArr = []
for (i in arr){//Инициализируем объекты
objArr[count] = {
    letter: i,
    freq: arr[i],
    father: null,
    code: "",
    left: false,
    right: false,
    leftSon: null,
    rightSon: null,
    son: true,
    isUsed: false,
    isMax: false
}
count++
}


if (str.length == 1){
    let obj = {
        char: str[0],
        code: "0"
    }
    console.log("Tab: ", obj)
    console.log("Coded string: ", obj.code)
    console.log("Decoded string: ", obj.char)
} else if (objArr.length == 1){
    let s = ""
    let d = ""
    for (let i = 0; i < objArr[0].freq; i++){
        s += "0"
        d += objArr[0].letter
    }
    console.log("Coded string: ", s)
    console.log("Decodes string: ", d)
} else {

let leaves = []
while (objArr.length !=1){//Строим дерево
let left  = findMin()
let right = findMin()
obj = new Object()
obj = {
    letter: left.letter + right.letter,
    freq: left.freq + right.freq,
    father: null,
    code: "",
    left: false,
    right: false,
    leftSon: left,
    rightSon: right
    }
left.father = obj
left.left = true
right.father = obj
right.right = true
if (left.son)
leaves.push(left)
if (right.son)
leaves.push(right)
    objArr.push(obj)
}   
let iter = 0
let Tab = []
let kod = []
let ch =""

function getTab(object){
    if (iter < leaves.length){
if (object.father != null){
    if (object.son){
        ch = object.letter
    }
    if (object.left){
        kod.push("0")
    } else {
        kod.push("1")
    }
    getTab(object.father)
} else {
    Tab[iter] = {
        char: ch,
        code: kod.reverse().join('')
    }
    kod.splice(0,kod.length)
    iter++
}
    } else {
        return
    }

}
for (let i  =0 ; i < leaves.length; i++){
getTab(leaves[i])
}

console.log("TAB: ",Tab)
let codedStr = ""//Кодирование строки
for (let i = 0; i < str.length; i++){
    for (let j = 0; j < Tab.length; j++){
        if (str[i]==Tab[j].char){
            codedStr += Tab[j].code
            break
        } 
    }
}
let dec = []//вспомогательный массив
for (let i = 0; i < Tab.length; i++){
    dec.push(Tab[i].char, Tab[i].code)
}

console.log("Coded string: ",codedStr)//выводим закодированную строку

let repeat = 0
let len = 1
let decodedStr = ""
for (let i = 0 ;  i < codedStr.length;){//декодирование
    if (dec.indexOf(codedStr.slice(i,len))!= -1){
        let idx = dec.indexOf(codedStr.slice(i,len))-1
        decodedStr += dec[idx]
        i += codedStr.slice(i,len).length
        len += codedStr.slice(i,len).length-repeat
        repeat = 0
    } else 
    len++
    repeat++
}

console.log("Decoded string: ",decodedStr)//выводим декодированную строку

function findMin(){//Функция для нахождения наименьшего по частоте элемента среди объектов
    let min = primalLen
    let idx = 0
for (let i = 0; i < objArr.length; i++){
if (objArr[i].freq < min){
    min = objArr[i].freq
    idx = i
        }
    }
    let obj = objArr[idx]
    objArr.splice(idx, 1)
    return obj
}

}
