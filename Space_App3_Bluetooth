
 import processing.serial.*;
 
 Serial serialPort;
 int valorX,valorY,indice,medio,anular;
 int boton1X= 200;
 int boton1Y= 600;
 int anchoBoton =200;
 int altoBoton = 100;
 int[] valores;
 
 int boton2X = 500;
 int boton2Y = 600;

 int boton3X = 800;
 int boton3Y = 600;
 int robotX =  600;
 int robotY = 300;
 boolean mision,robot,statusTraje,arrastrar;
 
 PImage status;
 
void setup() {
  
   size(1200,800);
   status = loadImage("status.png");
   println(Serial.list());
   serialPort = new Serial(this, "COM23", 9600);
   serialPort.bufferUntil('\n');
   
}

void draw() {


 background(180);  
 fill(0);
   ellipse(valorX,valorY, 50,50);
 
    String estadoGuante = serialPort.readStringUntil('\n');
   
  if(estadoGuante != null) {
    
   valores =int(split(estadoGuante,","));
   
   valorX = (int)map(valores[1],300,410,0,width);
   valorY = (int)map(valores[0],295,415,height,0);
   indice = valores[2];
   medio = valores[3];
   anular = valores[4];
   textSize(40);

   //println(estadoGuante);
   
   
  }
 
 fill(0);
 rectMode(CORNER);
 rect(boton1X,boton1Y,anchoBoton,altoBoton);
 rect(boton2X,boton2Y,anchoBoton,altoBoton);
 rect(boton3X,boton3Y,anchoBoton,altoBoton);
 
 
  if (valorX >= boton1X && valorX <= boton1X +anchoBoton && valorY >= boton1Y && valorY <= boton1Y+altoBoton) {
   
    fill(255,0,0);
    rectMode(CORNER);
    rect(boton1X,boton1Y,anchoBoton,altoBoton);
    if(indice == 1) {
    mision=true;
    println(mision);

    }
  
 }
 
 if(valorX>= boton2X && valorX <= boton2X + anchoBoton && valorY >= boton2Y && valorY <= boton2Y +altoBoton) {
      
   fill(255,0,0);
   rectMode(CORNER);
   rect(boton2X,boton2Y,anchoBoton,altoBoton);
   if(indice == 1) {
   robot = true;
   println(robot);
      
    }
   
 }
 
  if(valorX>= boton3X && valorX <= boton3X + anchoBoton && valorY >= boton3Y && valorY <= boton3Y +altoBoton) {
      
   fill(255,0,0);
   rectMode(CORNER);
   rect(boton3X,boton3Y,anchoBoton,altoBoton);
   if(indice == 1) {
   statusTraje = true;
   println(statusTraje);
      
    }
   
 }
 
   if(mision  /*robot == '1' && screenShot == '1'*/) {
    textSize(40);
    stroke(0);
    text("Estatus de la mision",300,300); 
    robot = false;
    statusTraje = false;
   
 }

  if(robot) {
    fill(0,255,0);
    rectMode(CENTER);
    rect(robotX, robotY,anchoBoton,altoBoton); 
    
    if(valorX >= robotX - anchoBoton/2 && valorX <= robotX+anchoBoton/2 && valorY >= robotY- altoBoton/2 && valorY <= robotY+ altoBoton/2){
     fill(120,255,120); 
     rect(robotX,robotY,anchoBoton,altoBoton);
     if (arrastrar){
       robotX= valorX;
       robotY= valorY;
     }
     
    }
    
  }
  
   if(statusTraje) {
    image(status,300,150,500,400);
    
     
     
   }
  
  if(indice == 0 && medio == 0 && anular == 1){
     if(mision && !robot && !statusTraje) {
      mision = false;
      robot = false;
      statusTraje= false; 
     }
     
     if(!mision && robot && !statusTraje) {
      mision = false;
      robot = false;
      statusTraje= false; 
     }
     
     if(!mision && !robot && statusTraje){
      mision = false;
      robot = false;
      statusTraje = false;
      
     }
  }
  
  if( indice == 1 && medio == 1 && anular == 0) {
   arrastrar = true;
    
  }
  
  if(indice == 0 && medio == 0 && anular== 0) {
   arrastrar = false;
   
    
  }
  
  
  
  
  

}


