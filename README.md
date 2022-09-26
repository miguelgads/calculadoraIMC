# calculadoraIMC

Calculadora IMC em react js simples


import React, {useState} from 'react';
import { View, Text, TextInput ,StyleSheet, TouchableOpacity, Alert } from 'react-native';


export default function App(){

  
  const [altura, setaltura]       = useState('');
  const [peso, setpeso]           = useState('');
  const [resultado, setResultado] = useState(0);
  const [result, setResult]             = useState('');

  const calcular = function(){
    
    
   setResultado(Number(peso)/(Number(altura)*Number(altura)));

    
   if(altura == '' || peso == ''){
      setResult('Digite um valor!')
      return;

    }

   if (resultado < 18.5){
      setResult('Abaixo do Peso')
      
   } else if(resultado < 25){
      setResult('Peso Normal')
    }else if (resultado < 30){
      setResult('Sobrepeso')
    }else if (resultado < 35){
      setResult('Obesidade grau 1')
    }else if (resultado < 40){
      setResult('Obesidade grau 2')
    }else  { 
      setResult('Obesidade grau 3')
    }
    
    

  }
  
   function limpar(){
    setResultado(0)
    setResult('')
    setaltura('')
    setpeso('')

   limparInputs();
  }

return(
    <View style={style.container}>
      
      <View style={style.titulo}>

        <Text style={style.cptitulo}>CALCULADORA DE IMC</Text>
          
      </View>

      <View style={style.entrada}>

        <TextInput style={style.cpInput}
          placeholder = 'Altura'
          keyboardType = 'characters'
          value={altura}
          onChangeText={(valor) => {setaltura(valor)}} 
        />

         <TextInput style={style.cpInput}
          placeholder = 'Peso'
          keyboardType = 'numeric'
          value={peso}
          onChangeText={(valor) => {setpeso(valor)}} 
        />

      </View>

      

      <View style={style.calculo}>

        <TouchableOpacity 
        style={style.botao} 
        onPress={calcular}>
          
        <Text style={style.textBotao} >Calcular</Text>
        </TouchableOpacity>

        <TouchableOpacity 
        style={style.botao} 
        onPress={limpar}>
        
        <Text style={style.textBotao}>Limpar</Text>
        </TouchableOpacity>

      </View>

      <View style={style.resultado}>

        <Text style={style.textResultado}>
          
          IMC = {(resultado.toFixed(2))}
        </Text>

        <Text style={style.textResultado}>
          {result}
        </Text>
        
      </View>

    </View>
  );
}

//area formatacao
const style = StyleSheet.create({

container: {
  
flex:1,

borderColor: 'Black',
alignItems: 'center',
marginTop: 100,
},
  
titulo:{

paddingTop: 30,


},
  
cptitulo:{
    
fontSize: 25,
fontWeight: "bold"

},

entrada: {

paddingTop: 30,
width: 250,

 
},  

cpInput: {

fontSize: 25,
textAlign: 'center',
borderWidth: 3,
borderColor: 'red',
marginTop: 15,
color: "grey"




      
},

calculo: {
      
marginTop: 30,
width: 250,
flexDirection: 'row',
justifyContent: 'center',

},  

botao: {

justifyContent: 'center',
backgroundColor: 'red',
width: 111,
height: 40,
borderRadius: 30,
margin: 10,

},  

textBotao: {
        
textAlign: 'center',
fontSize: 18,
fontWeight: "bold",
            
},

resultado: {
paddingTop: 8,

},  

textResultado: {

textAlign: 'center',
lineHeight: 50,
fontSize: 20,
marginTop: 5,

fontWeight: 'bold',
      },

});
