# NeuroPy <br>
NeuroPy library written in python to connect, interact and get data from NeuroSky's MindWave EEG headset. <br>
# Usage <br>

1. Importing the module: from `NeuroPy.NeuroPy import NeuroPy` <br>
2. Initializing: `neuropy = NeuroPy(port)`<br>
3. After initializing, if required the callbacks can be set <br>
4. Then call `neuropy.start()` method, it will start fetching data from mindwave.<br>
5. To stop call `neuropy.stop()`<br>

# Obtaining Data from Device <br>

### Obtaining value: 
`attention = neuropy.attention` to get value of attention_ <br>
## Other Variable 
    attention, meditation, rawValue, delta, theta, lowAlpha, highAlpha, lowBeta, highBeta, lowGamma, midGamma and poorSignal
### Setting callback:
A call back can be associated with all the above variables so that a function is called when the variable is updated. Syntax:

    setCallBack("[variable]",callback_function)

for eg. to set a callback for attention data the syntax will be
    
    setCallBack("attention",callback_function)

### Other Variables: 
    attention, meditation, rawValue, delta, theta, lowAlpha, highAlpha, lowBeta, highBeta, lowGamma, midGamma and poorSignal

### save to CSV
    saveToCSV()
### args that you can pass in this function
    time #how long do you want to fetch the data
    path #path where to save the csv file
    mode #writing mode of the CSV file eg. w, W+, a etc
    delay # delay for fetching next data

## Sample Program 1 (Access via callback)
    from NeuroPy.NeuroPy import NeuroPy
    from time import sleep

    neuropy = NeuroPy('COM4') 

    def attention_callback(attention_value):
        """this function will be called everytime NeuroPy has a new value for attention"""
        print ("Value of attention is: ", attention_value)
        return None

    neuropy.setCallBack("attention", attention_callback)
    neuropy.start()

## Sample Program 2 (Access via object)
    from NeuroPy.NeuroPy import NeuroPy
    from time import sleep

    neuropy = NeuroPy('COM4') 
    neuropy.start()

    while True:
        if neuropy.meditation > 70: # Access data through object
            neuropy.stop() 
        sleep(0.2) # Don't eat the CPU cycles

## Sample Program 3 (Save to csv)
    from NeuroPy.NeuroPy import NeuroPy
    from time import sleep

    neuropy = NeuroPy('COM4') 
    neuropy.start()
    neuropy.saveToCSV()
    neuropy.stop()
        
# Python Compatibility
Python 3.x
