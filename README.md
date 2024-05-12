# Foundry-Scroll演示

在此示例中，我们将在 Sepolia 或 Scroll 上启动虚拟智能合约，并从相反的链与其进行交互。我们将使用`ScrollMessenger`部署在 Sepolia 和 Scroll 上的

# 准备

1 : 安装foudnry
  
**`curl -L https://foundry.paradigm.xyz | bash`**

2 : 安装scroll包
  
**`npm install @scroll-tech/contracts`**

## 部署合约
一 ： 通过运行以下命令设置环境变量：
**`export RPC_URL=<你的 RPC 端点>`**
**`export PRIVATE_KEY=<你的钱包私钥>`**

二 ： 编译
**`forge build`**

三：部署
**`forge create --rpc-url=$RPC_URL --private-key=$PRIVATE_KEY ./src/L1.sol:GreeterOperator `**

**`forge create --rpc-url=$RPC_URL --private-key=$PRIVATE_KEY ./src/L2.sol:Greeter`**

四 ： 调用
**`cast send --value 0.01ether  GreeterOperator合约地址 "executeFunctionCrosschain(address,address,uint256,string,uint32)" scrollMessengerAddress Greeter合约地址 0 "This message was cross-chain!" 1000000`**

  `scrollMessengerAddress`：这取决于您部署`GreeterOperator`合约的位置
    -   如果您将其部署在 Sepolia 上，请使用`0x50c7d3e7f7c656493D1D76aaa1a836CedfCBB16A`.如果您部署在 Scroll Sepolia 上，请使用`0xBa50f5340FB9F3Bd074bD638c9BE13eCB36E603d`.
