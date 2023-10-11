# I2C Unit Driver
Driver for working with I2C(TWI) unit of AVR microcontroller.

### Version : 0.7.0

- #### Type : Embedded Software.

- #### Support : AVR microcontroller.

- #### Program Language : C

- #### Properties :

### Initialization and de-initialization functions:
```c++
void I2C_Init(void); /* Function for Initialize the I2C peripheral. */
void I2C_DeInit(void); /* Function for Deinitialize the I2C peripheral. */
void I2C_SetAddress(uint8_t address); /* Function for self I2C address (use when MCU is slave only) */
```
### Operation functions:
```c++  
uint8_t I2C_IsDeviceReady(uint8_t dev_address , uint16_t trials , uint16_t time_out); /* Function for check connected device */
StatusTypeDef I2C_Master_Transmit(uint8_t dev_address , uint8_t *data , uint32_t quantity , uint16_t time_out); /* Function for transmit data to i2c device */
StatusTypeDef I2C_Master_Receive(uint8_t dev_address , uint8_t *data , uint32_t quantity , uint16_t time_out); /* Function for receive data from i2c device */
StatusTypeDef I2C_Mem_Write(uint8_t dev_address , uint32_t mem_address , uint8_t mem_add_size , uint8_t *mem_data , uint32_t quantity , uint16_t time_out); /* This function is for write data to external memory */
StatusTypeDef I2C_Mem_Read(uint8_t dev_address , uint32_t mem_address , uint8_t mem_add_size , uint8_t *mem_data , uint32_t quantity , uint16_t time_out ); /* This function is for read data from external memory */
StatusTypeDef I2C_Mem_Erase(uint8_t dev_address , uint32_t mem_address , uint8_t mem_add_size , uint32_t quantity , uint16_t time_out); /* This function is for erase external memory */
``` 
### Macros:
```c++   
#define _F_SCL
#define _PRESCALER
``` 

## How to use this library

### The I2C Unit driver can be used as follows:
#### 1.  Add .h and source file in project.      
#### 2.  Config SCL/SDA GPIO as output in your project.  

```c++  
DDRC = (1 << SCL_PIN)|(1 << SDA_PIN);
```  
#### 3.  Config SCL clock in 'i2c_unit_conf.h' header, for example:   
   
```c++  
#define _F_SCL      100000UL 
#define _PRESCALER  _PRE1 
   
``` 
      
#### 4.  Use operation methods, for example:  
#### Example:  
```c++  
 
int main(void)
{
    DDRC = (1 << SCL_PIN)|(1 << SDA_PIN);
    
    I2C_Init();
    
    while (1) 
    {
  
      I2C_Master_Transmit(0xA0 , "MyData" , 6 , 100); /* 0xA0 is device address, "MyData" is data for transmit, 6 is data length, 100 is timeout */
    
    }
}
   
``` 
#### Other Examples:  
- Used in MPU6050 Library : [MPU6050 Library](https://github.com/Majid-Derhambakhsh/MPU6050)  
- Used in i2c-eeprom Library : [i2c-eeprom Library](https://github.com/Majid-Derhambakhsh/i2c-eeprom)  
- Used in DS1307 Library : [DS1307 Library](https://github.com/Majid-Derhambakhsh/DS1307-Library)  
and more ...

## Tests performed:
- [X] Run on AVR

#### Developer: Majid Derhambakhsh
