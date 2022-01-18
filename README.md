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
