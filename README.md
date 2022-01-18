- 👋 Hi, I’m Pham Xuan Ky from VIET NAM
- 👀 I’m interested in Coding for PLC, Arduino , IOT programming
- 🌱 I’m currently learning and improving coding
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me by phamxuanky82@gmail.com

<!---
XuanKyVN/XuanKyVN is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

MODBUS MASTER LIBRARY RS485 

#######################################
# Syntax Coloring Map For ModbusMaster
#######################################

#######################################
# Datatypes (KEYWORD1)
#######################################

ModbusMaster	KEYWORD1

#######################################
# Methods and Functions (KEYWORD2)
#######################################

lowWord	KEYWORD2
highWord	KEYWORD2
LONG	KEYWORD2

begin	KEYWORD2

getResponseBuffer	KEYWORD2
clearResponseBuffer	KEYWORD2
setTransmitBuffer	KEYWORD2
clearTransmitBuffer	KEYWORD2

readCoils	KEYWORD2
readDiscreteInputs	KEYWORD2
readHoldingRegisters	KEYWORD2
readInputRegisters	KEYWORD2
#---------------------
readHoldingRegisterUInt16 KEYWORD2
readHoldingRegisterUInt32 KEYWORD2
readHoldingRegisterUInt64 KEYWORD2
readHoldingRegisterInt16 KEYWORD2
readHoldingRegisterInt32 KEYWORD2
readHoldingRegisterInt64 KEYWORD2
readHoldingRegisterFloat32 KEYWORD2

readInputRegisterUInt16 KEYWORD2
readInputRegisterUInt32 KEYWORD2
readInputRegisterUInt64 KEYWORD2
readInputRegisterInt16 KEYWORD2
readInputRegisterInt32 KEYWORD2
readInputRegisterInt64 KEYWORD2
readInputRegisterFloat32 KEYWORD2

readDatetimeHRegister KEYWORD2
readDatetimeIRegister KEYWORD2
writeDatetimeHR KEYWORD2

writeSingleCoil	KEYWORD2
writeSingleRegister	KEYWORD2
writeMultipleCoils	KEYWORD2
writeMultipleRegisters	KEYWORD2
# NEW KeyWord BY KYCONG----------
writeMultipleRegistersU32	KEYWORD2
writeMultipleRegistersU64	KEYWORD2
uint8_t writeMultipleRegistersU64_1 KEYWORD2
uint8_t writeMultipleRegistersU64_2 KEYWORD2
writeMultipleRegistersFloat32	KEYWORD2

writeSingleRegisterInt16	KEYWORD2
writeMultipleRegistersInt32 KEYWORD2
writeMultipleRegistersInt64 KEYWORD2
writeMultipleRegistersInt64_1 KEYWORD2
writeMultipleRegistersInt64_2 KEYWORD2
#-------------------------------------------
maskWriteRegister	KEYWORD2
readWriteMultipleRegisters	KEYWORD2

#######################################
# Constants (LITERAL1)
#######################################

ku8MBIllegalFunction	LITERAL1
ku8MBIllegalDataAddress	LITERAL1
ku8MBIllegalDataValue	LITERAL1
ku8MBSlaveDeviceFailure	LITERAL1

ku8MBSuccess	LITERAL1
ku8MBInvalidSlaveID	LITERAL1
ku8MBInvalidFunction	LITERAL1
ku8MBResponseTimedOut	LITERAL1
ku8MBInvalidCRC	LITERAL1
result	LITERAL1

//--------------// USING LIBRARY-----------

Remove IF in the command below, because they are my program onlu

//---------------------------------------------------
void ModbusUpdate() {
if (MbEnb=="Enable"){
  // clear status
    for(int i=0;i<20;i++){
    mbRStatus[i]=0;
    }
    
 //-----------------------Holding Register Read--------------------------------
if (HrR2_num>0){
for (int i=0;i<HrR2_num;i++){
vHrR16[i]= node.readHoldingRegisterUInt16(HrR2[i]);
if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR2: "+ String(i) + ": " + String(vHrR16[i]));
      mbRStatus[0]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR2 that bai!");
       mbRStatus[0]=2;
    }  delay(20);
  } 
}

if (HrR3_num>0){
for (int i=0;i<HrR3_num;i++){
 vHrR32[i] = node.readHoldingRegisterUInt32(HrR3[i]);
if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR3: "+ String(i) + ": " + String(vHrR32[i]));
      mbRStatus[1]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR3 that bai!");
       mbRStatus[1]=2;
    }delay(20);
} 
}

if (HrR4_num>0){ //Uint64

for (int i=0;i<HrR4_num;i++){
  // docSend Modbus theo Chu ky nhe de gioi han thoi gian ko dung ham delay qua lau
    vHrR64_L[i] = node.readHoldingRegisterUInt32(HrR4[i]);
    vHrR64_H[i] = node.readHoldingRegisterUInt32(HrR4[i]+2);
    if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR4: "+ String(i) + ": " + String(vHrR64_L[i]));
      mbRStatus[2]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR4 that bai!");
       mbRStatus[2]=2;
    }    delay(20);
   } 
}
//---------
if (HrR5_num>0){ // float
for (int i=0;i<HrR5_num;i++){
 vHrRFloat[i]=node.readHoldingRegisterFloat32(HrR5[i]);
 if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR5: "+ String(i) + ": " + String(vHrRFloat[i]));
      mbRStatus[3]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR5 that bai!");
       mbRStatus[3]=2;
    }delay(20);
} 
}


if (HrR6_num>0){//int16
for (int i=0;i<HrR6_num;i++){
 vHrR6[i] = node.readHoldingRegisterInt16(HrR6[i]) ;
 if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR6: "+ String(i) + ": " + String(vHrRFloat[i]));
      mbRStatus[4]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR6 that bai!");
       mbRStatus[4]=2;
    }delay(20);
} 
}

if (HrR7_num>0){ //Int32
for (int i=0;i<HrR7_num;i++){
  vHrR7[i] = node.readHoldingRegisterInt32(HrR7[i]);
  if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR7: "+ String(i) + ": " + String(vHrR7[i]));
      mbRStatus[5]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR7 that bai!");
       mbRStatus[5]=2;
    }delay(20);   
} 
}


if (HrR8_num>0){ //int64
for (int i=0;i<HrR8_num;i++){
    vHrR8_L[i] = node.readHoldingRegisterInt32(HrR8[i]); 
    vHrR8_H[i] = node.readHoldingRegisterInt32(HrR7[i]+2);
   if (node.result == node.ku8MBSuccess){
     //Serial.println("Value HrR8: "+ String(i) + ": " + String(vHrR8_L[i]));
      mbRStatus[6]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR8 that bai!");
       mbRStatus[6]=2;
    }delay(20);   
} 
}

//-----------------------INPUT Register Read 3xxxx------------------------------

if (IrR2_num>0){
for (int i=0;i<IrR2_num;i++){
  vIrR16[i] = node.readInputRegisterUInt16(IrR2[i]); 
  if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR2: "+ String(i) + ": " + String(vIrR16[i]));
      mbRStatus[7]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR2 that bai!");
       mbRStatus[7]=2;
    }delay(20);      
} 
}

if (IrR3_num>0){
uint16_t i16data[2];
for (int i=0;i<IrR3_num;i++){
     vIrR32[i] = node.readInputRegisterUInt32(IrR3[i]);
     if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR3: "+ String(i) + ": " + String(vIrR32[i]));
      mbRStatus[8]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR3 that bai!");
       mbRStatus[8]=2;
    }delay(20);      
    } 
}

if (IrR4_num>0){ //Uint64
for (int i=0;i<IrR4_num;i++){
    vIrR64_L[i] = vIrR32[i] = node.readInputRegisterUInt32(IrR4[i]);
    vIrR64_H[i] = vIrR32[i] = node.readInputRegisterUInt32(IrR4[i]+2);
    if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR4: "+ String(i) + ": " + String(vIrR64_L[i]));
      mbRStatus[9]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR4 that bai!");
       mbRStatus[9]=2;
    }delay(20);      
    } 
}
//---------
if (IrR5_num>0){ // float
for (int i=0;i<IrR5_num;i++){
   vIrRFloat[i]= node.readInputRegisterFloat32(IrR5[i]);
   if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR5: "+ String(i) + ": " + String(vIrRFloat[i]));
      mbRStatus[10]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR5 that bai!");
       mbRStatus[10]=2;
    }delay(20);      
  } 
}

if (IrR6_num>0){ //int16
for (int i=0;i<IrR6_num;i++){
      vIrR6[i] = node.readInputRegisterInt16(IrR6[i]);
      if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR6: "+ String(i) + ": " + String(vIrR6[i]));
      mbRStatus[11]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR6 that bai!");
       mbRStatus[11]=2;
    }delay(20);      
       
    } 
}

if (IrR7_num>0){ //int32
for (int i=0;i<IrR7_num;i++){
      vIrR7[i] = node.readInputRegisterInt32(IrR7[i]);
      if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR7: "+ String(i) + ": " + String(vIrR7[i]));
      mbRStatus[12]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR7 that bai!");
       mbRStatus[12]=2;
    }delay(20);      
   } 
}


if (IrR8_num>0){ //int64
for (int i=0;i<IrR8_num;i++){
    vIrR8_L[i] = node.readInputRegisterInt32(IrR8[i]);
    vIrR8_H[i] = node.readInputRegisterInt32(IrR8[i]);
    if (node.result == node.ku8MBSuccess){
     //Serial.println("Value IrR8: "+ String(i) + ": " + String(vIrR8_L[i]));
      mbRStatus[13]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" IrR8 that bai!");
       mbRStatus[13]=2;
    }delay(20);       
  } 
}
//-------------------------DiscreteInput and Coil READ
if (DiR1_num>0){
for (int i=0;i<DiR1_num;i++){
  // docSend Modbus theo Chu ky nhe de gioi han thoi gian ko dung ham delay qua lau
  uint8_t result1 = node.readDiscreteInputs(DiR1[i], 1);
    if (result1 == node.ku8MBSuccess){
     vDiR1[i] = node.getResponseBuffer(0);   
     //Serial.println("Value DrR1: "+ String(i) + ": " + String(vDiR1[i]));
      mbRStatus[14]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" DiR1 that bai!");
       mbRStatus[14]=2;
    }delay(20); 
   } 
}
if (ColR1_num>0){
for (int i=0;i<ColR1_num;i++){
  // docSend Modbus theo Chu ky nhe de gioi han thoi gian ko dung ham delay qua lau
  uint8_t result1 = node.readCoils(ColR1[i], 1);
    if (result1 == node.ku8MBSuccess){
    vColR1[i] = node.getResponseBuffer(0); //uint8, ON =1; OFF = 0     
     //Serial.println("Value CoilR"+ String(i) +": "+ String(vColR1[i]));
     mbRStatus[15]=1;
    }else{
      //Serial.println("Ket noi RS485 ID"+ String(IDsel)+" ColR1 that bai!");
      mbRStatus[15]=2;
    }delay(20); 
    } 
}


if (HrR9_num>0){ //int64
for (int i=0;i<HrR9_num;i++){
uint8_t result1 = node.readDatetimeHRegister(HrR9[i]);
if (result1==node.ku8MBSuccess){
Serial.print(node.Day);Serial.print(":");
Serial.print(node.Month);Serial.print(":");
Serial.println(node.Year);Serial.print("  ");
Serial.print(node.Hours); Serial.print(":");
Serial.print(node.Minute); Serial.print(":");
uint8_t second_read= (String(node.miliSecond).substring(0,2)).toInt();
Serial.println(second_read);

vHrR9[i]=String(node.Day)+"/"+String(node.Month)+"/"+String(node.Year)+"/" + String(node.Hours)+":"+String(node.Minute)+":"+String(second_read);
mbRStatus[16]=1;     
}else{//Serial.println("fail to read date time");
  mbRStatus[16]=2;
  }delay(20); 
  } 
}
//--------
if (IrR9_num>0){ //int64
for (int i=0;i<IrR9_num;i++){
uint8_t result1 = node.readDatetimeIRegister(IrR9[i]);
if (result1==node.ku8MBSuccess){
Serial.print(node.Day);Serial.print(":");
Serial.print(node.Month);Serial.print(":");
Serial.println(node.Year);Serial.print("  ");
Serial.print(node.Hours); Serial.print(":");
Serial.print(node.Minute); Serial.print(":");
uint8_t second_read= (String(node.miliSecond).substring(0,2)).toInt();
Serial.println(second_read);

vIrR9[i]=String(node.Day)+"/"+String(node.Month)+"/"+String(node.Year)+"/" + String(node.Hours)+":"+String(node.Minute)+":"+String(second_read);
mbRStatus[17]=1;     
}else{//Serial.println("fail to read date time");
  mbRStatus[17]=2;
  }delay(20); 
  } 
}
//-----------




MBreadStatus = testmbRStatus(2,mbRStatus);
//Serial.println(MBreadStatus);
uint8_t idchoose;
  if (IDnum>1&&IDsel<=IDnum-1){ // i chay 0,1,2
      idchoose=IDsel+1;
  }else {idchoose=1;}
//-----------------------------
String msg1;// message to be send 
serializeJson(mainDoc, msg1); //string

if (WifiConnected){  //Blynk and MQTT only working when Wifi connected
  
mqttPublish(idchoose,msg1);
Blynkupdate(IDsel);
}
//----------------------------
 if (IDread==1){ //Read ID1
  webSocket.broadcastTXT(msg1);
  }
//------------------------------End Enable/Disable-----------
if (logenb){
handle_fbMbus(true);
}else{handle_fbMbus(false);}

if(IDnum>1){
IDsel=IDsel+1;
if(IDsel>IDnum){IDsel=1;}
mbEnb_ReadFlash();
Mbconfig(); // so noned reset whenconfig
MbconfigID();
mbReg_ReadFlash(); // doc dia chi cac thanh ghi 
}else{IDsel=ID;}
}

}// END OF PROGRAM-------------------
void modbuswrite(){
// ----------Unsigne Int------------
  // clear status
    for(int i=0;i<12;i++){
    mbWStatus[i]=0;
    }

if (enbHrW[0]==1){ //16bit
    uint8_t result1= node.writeSingleRegister(HrW16Add, vHrW16);
    if (result1 == node.ku8MBSuccess){
    Serial.println("Value HW register 16Uint ID "+String(IDsel)+":" + String(vHrW16));
     mbWStatus[0]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR16 UInt that bai!");
      mbWStatus[0]=2;
    }  
enbHrW[0]=0; 
}//------------
if (enbHrW[1]==1){ //32Bit
  uint8_t result1= node.writeMultipleRegistersU32(HrW32Add, vHrW32);
 if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR32 UInt ID "+String(IDsel)+":" + String(vHrW32));
     mbWStatus[1]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HR32 UInt that bai!");
      mbWStatus[1]=2;
    }        
    enbHrW[1]=0;
} //----------------------------
if (enbHrW[2]==1){ // 64bit Uint writing
   uint8_t result1=node.writeMultipleRegistersU64_1(HrW64Add, BufferHrW); 
    if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR64 UInt for  ID "+String(IDsel)+":" + String(BufferHrW[0]));
    Serial.println("Value HR64 UInt for  ID "+String(IDsel)+":" + String(BufferHrW[1]));
    Serial.println("Value HR64 UInt for  ID "+String(IDsel)+":" + String(BufferHrW[2]));
    Serial.println("Value HR64 UInt for  ID "+String(IDsel)+":" + String(BufferHrW[3])); 
    mbWStatus[2]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrRW64 UInt that bai!");
      mbWStatus[2]=2;
    }        
    enbHrW[2]=0;
}//---------------------------
if (enbHrW[3]==1){ // Float 32Bit
    uint8_t result1=node.writeMultipleRegistersFloat32(HrWFloatAdd, vHrWFloat);  
     if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR Float Int ID "+String(IDsel)+":" + String(vHrWFloat));
     mbWStatus[3]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HR Float that bai!");
      mbWStatus[3]=2;
    }        
    enbHrW[3]=0;
}//------------------------------------
// SIGNED INT +-

if (enbHrW[4]==1){ //16bit
    uint8_t result1= node.writeSingleRegisterInt16(HrW16IAdd, vHrWI16);
     if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR16 Int ID "+String(IDsel)+":" + String(vHrWI16));
     mbWStatus[4]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR16 Int that bai!");
      mbWStatus[4]=2;
    }  
enbHrW[4]=0; 
}//------------
if (enbHrW[5]==1){ //32Bit
  uint8_t result1= node.writeMultipleRegistersInt32(HrW32IAdd, vHrWI32);
    if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR32 Int ID "+String(IDsel)+":" + String(vHrWI32));
     mbWStatus[5]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR32 Int that bai!");
    mbWStatus[5]=2;
    }      
    enbHrW[5]=0;
} //----------------------------
if (enbHrW[6]==1){ // 64bit int writing
  uint8_t result1=node.writeMultipleRegistersInt64_1(HrW64IAdd, BufferHrWInt); // Buffer[0-3]
  if (result1 == node.ku8MBSuccess){
    Serial.println("Value HR64 Int for  ID "+String(IDsel)+":" + String(BufferHrWInt[0]));
    Serial.println("Value HR64 Int for  ID "+String(IDsel)+":" + String(BufferHrWInt[1]));
    Serial.println("Value HR64 Int for  ID "+String(IDsel)+":" + String(BufferHrWInt[2]));
    Serial.println("Value HR64 Int for  ID "+String(IDsel)+":" + String(BufferHrWInt[3])); 
    mbWStatus[6]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrRW64 Int that bai!");
    mbWStatus[6]=2;
    }         
    enbHrW[6]=0;
} //---------------------------


if (SingleCoil==1){ // Write Sigle Coil
    uint8_t result1 = node.writeSingleCoil(coilWadd, BufferHrW[0]);
    if (result1 == node.ku8MBSuccess){
    Serial.println("Value Sigle Coil ID "+String(IDsel)+":" + String(BufferHrW[0]));
     mbWStatus[7]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR2 that bai!");
    mbWStatus[7]=2;
    }  
SingleCoil=0;
}
//------------------------------------
if (MultiCoil==1){ // Write Sigle Coil
node.setTransmitBuffer(0,BufferHrW[0]);
uint8_t numcoilwrite=0;
uint8_t vColW =   BufferHrW[0];
if (vColW<16){numcoilwrite=4;}else if (vColW<256&&vColW>15){numcoilwrite=8;}else if (vColW<65536&& vColW>255){numcoilwrite=16;}
uint8_t result1 = node.writeMultipleCoils(coilsWadd, numcoilwrite);//Ghi tu Bit thu 6 , do dai 8 bit 255
node.clearTransmitBuffer();
if (result1 == node.ku8MBSuccess){
    Serial.println("Value Multi Coils ID "+String(IDsel)+":" + String(vColW));
     mbWStatus[8]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR2 that bai!");
      mbWStatus[8]=2;
    }
    MultiCoil=0;   
} 
//------------------------
if ( enbHrW[7]==1){ // Write Bit in MAP Address, 
uint8_t result1 = node.maskWriteRegister(AddHrMask, andMask,orMask);//Ghi tu Bit thu 6 , do dai 8 bit 255
node.clearTransmitBuffer();
if (result1 == node.ku8MBSuccess){
    Serial.println("Value Mas Address ID "+String(IDsel)+":" + String(AddHrMask));
     mbWStatus[9]=1;
    }else{
      Serial.println("Ket noi RS485 ID"+ String(IDsel)+" HrR2 that bai!");
      mbWStatus[9]=2;
    }
    enbHrW[7]=0;   
} 
if ( enbHrW[8]==1){ 
uint8_t result1 = node.writeDatetimeHR(AddDtime,day_val,month_val,year_val,hour_val,min_val,sec_val);
if (result1==node.ku8MBSuccess){
Serial.println("write date time "+String(AddDtime)+" ok");
mbWStatus[10]=1;
}else{Serial.println("fail to write date time");mbWStatus[10]=1;}
enbHrW[8]=0;
}

MBwriteStatus = testmbRStatus(2,mbWStatus);
if(MBwriteStatus){Serial.println("Write successfull");}else{Serial.println("Write Fail");}
}



 
