wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
chmod +x ./Miniconda3-latest-Linux-x86_64.sh 
./Miniconda3-latest-Linux-x86_64.sh 

cd ~ && mkdir fisco && cd fisco

chmod u+x build_chain.sh
./build_chain.sh -l 127.0.0.1:4 -p 30300,20200,8545
git clone https://github.com/FISCO-BCOS/python-sdk
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
conda init

ipfs init
ipfs daemon &

./build_chain.sh -l 127.0.0.1:4 -p 30300,20200,8545
bash nodes/127.0.0.1/start_all.sh

pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple


./bin/solc/solc --abi --bin contracts/ -o contracts/ --overwrite
python console2.py deploy MedicalData
python console2.py deploy AuditTrail
python console2.py deploy ZKProofVerifier

on block : 1,address: 0x882be29b2d5ac85d6c476fa3fd5f0cae4b4585cc 
save new address MedicalData -> 0x882be29b2d5ac85d6c476fa3fd5f0cae4b4585cc
address save to file:  bin/contract.ini
INFO >>  transaction from account : 0x2de5c210370daef452eb610af76c3a293ae1661f
INFO >>  receipt logs : 
INFO >> transaction hash :  0xef28192d7354f60139834c74951ba27901357c6f7a221231176016b23b4c216e


on block : 2,address: 0xdd14238434dc066e8ca48c2411b007176cbc514e 
save new address AuditTrail -> 0xdd14238434dc066e8ca48c2411b007176cbc514e
address save to file:  bin/contract.ini
INFO >>  transaction from account : 0x2de5c210370daef452eb610af76c3a293ae1661f
INFO >>  receipt logs : 
INFO >> transaction hash :  0x947d67128edddfa7f621e9c25a8551e9a197e52213b50ad557bad4f5efafc129


on block : 3,address: 0x7141d14b169e6aa4461094d2a6299f306c5c8b1f 
save new address ZKProofVerifier -> 0x7141d14b169e6aa4461094d2a6299f306c5c8b1f
address save to file:  bin/contract.ini
INFO >>  transaction from account : 0x2de5c210370daef452eb610af76c3a293ae1661f
INFO >>  receipt logs : 
INFO >> transaction hash :  0xba08cbe528248b5773f5398e53803b04cd1aa1f67b44f167f5e34282cec001b6
MedicalData = 0x882be29b2d5ac85d6c476fa3fd5f0cae4b4585cc
AuditTrail = 0xdd14238434dc066e8ca48c2411b007176cbc514e
ZKProofVerifier = 0x7141d14b169e6aa4461094d2a6299f306c5c8b1f

0x557346caeb4261aed980b30f60021849fd0aa8ada419c76e750dcfa558e6d69c