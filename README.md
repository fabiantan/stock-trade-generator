# This is the KPL Stock Trade Generator

To run this code:

1) Perform a git clone:
 git clone https://github.com/fabiantan/stock-trade-generator/

2) Run the code:
cd stock-trade-generator
mvn assembly:assembly
java -cp target/StockTradeGenerator-1.0.0-complete.jar -Dstream-name=kinesis_start_3 -Dbackpressure-size=50000 -Dbackpressure-delay=500 com.amazonaws.services.kinesis.application.producer.Generator


What Ec2 instance type should you use?
- To max out a 10 shard kinesis stream (10MBps), use a c3.4xlarge.
- If I were to use a c3.2xlarge, I could only max out 7.5 MBps of write throughput to a 10 shard Kinesis Stream
- If I were to use a m3.xlarge, I could only max out 4 MBps of write throughput to a 10 shard Kinesis Stream

What is throughput_Switch?
It enables 5 minutes interval of changing throughput.
From a minimum of 5MBps to 10MBps (or more)
Currently, you can only use option 1.


To execute consistent traffic, use the "backpressure-size" and "backpressure-delay" settings
