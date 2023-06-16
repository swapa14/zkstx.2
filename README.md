# zkstx.2
// 获取 zkSync 1.0 tx 数量
function getZkSyncTxCount(address) {
  const api_url = "https://api.zksync.io/api/v0.2/accounts/" + address;
  try {
    const result = JSON.parse(UrlFetchApp.fetch(api_url));
    const nonce = result["result"]["committed"]["nonce"];
    return nonce;
  } catch (e) {
    Logger.log(`Nonce 获取失败, ${e}`);
    return 0;
  }
}

// 2.0数据
// ❗️ 请修改此处的RPC为私有RPC，如 Infura 或 Alchemy，否则很容易超时报错
// 定义 RPC_MAP 变量
const RPC_MAP = {
  "zks":"https://zksync2-mainnet.zksync.io"
};

method: "post",
    payload: JSON.stringify({
      "jsonrpc": "2.0",
      "method": "eth_getBalance",
      "params": [walletAddress, "latest"],
      "id": 1
    }),
    contentType: "application/json",
    muteHttpExceptions: true
  });
  let result = JSON.parse(response.getContentText());
  let balance = result.result;
  return parseInt(balance, 16) / 10 ** 18;
}
