บทสรุป

การสร้างแอปพลิเคชันที่ติดต่อกับ Blockchain ได้ มาถึงตอนนี้เราก็ได้ DApp ตัวหนึ่ง ที่มีครบ 3 องค์ประกอบคือ UI + Smart Contract + Blockchain

ในแอปพลิเคชันที่สร้างด้วย JavaScript หรือ Node.js เราจะติดต่อกับ Ethereum ได้โดยใช้ Package ชื่อว่า web3 หลังจากติดต่อสำเร็จ เราสามารถดึงข้อมูลต่าง ๆ 
เช่น Account (web3.eth.accounts()) เป็นต้น รวมถึงสร้าง Transaction ส่งเงินและข้อมูลไปมาระหว่าง Account (web3.eth.sendTransaction()) ได้

สำหรับ Smart Contract ในที่นี้ได้ใช้ Package ที่ชื่อว่า @truffle/contract (TruffleContract) มาช่วยสร้าง Contract instance ซึ่งเป็น Object 
ที่ทำให้เราสามารถเรียกใช้ฟังก์ชันต่าง ๆ ตามที่ประกาศใน Smart Contract ด้วย ซึ่ง Package นี้ทำให้เราสามารถสร้าง Instance ได้อย่างสะดวก 
เพราะมันต้องการข้อมูลเพียงตัวเดียว คือ Truffle Artifact เท่านั้น

นอกจากนี้ TruffleContract ยังช่วยดึง Address ของ Smart Contract จาก Truffle Artifact มาใช้ให้เราอัตโนมัติ 
ในกรณีที่เราได้ Deploy Contract ใน Blockchain มากกว่า 1 ตัว เราสามารถเลือก Network ให้ TruffleContract ดึง Address ไปใช้อย่างถูกต้อง
โดยส่ง Provider ที่สร้างจาก web3 ไปให้ฟังก์ชัน contractInstance.setProvider()

สำหรับการเรียกใช้ฟังก์ชันที่ประกาศใน Smart Contract ต้องเรียกใช้ให้ถูกต้อง เพราะว่ามีวิธีการเรียกใช้อยู่ 2 แบบ คือ แบบ Call ใช้กับฟังก์ชันที่ทำหน้าที่ดึงข้อมูลอย่างเดียว 
และแบบ Send Transaction ใช้กับฟังก์ชันที่ทำหน้าที่แก้ไขข้อมูลในระบบ หากเรียกใช้ไม่ถูกต้อง จะได้ผลลัพธ์ที่ไม่ได้เป็นไปตามที่ต้องการ อย่างการเรียกฟังก์ชันแก้ไขข้อมูลแบบ 
Call ข้อมูลใน Smart Contract จะไม่ถูกเปลี่ยนแปลง และการเรียกใช้ฟังก์ชันดึงข้อมูลแบบ Send Transaction จะทำให้เกิด Transaction ขึ้น แต่เราจะไม่สามารถรับค่าได้เลย
