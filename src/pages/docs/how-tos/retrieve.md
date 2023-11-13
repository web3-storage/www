## Retrieve

## How to retrieve data from web3.storage

In this how-to guide, you'll learn several methods for retrieving data from web3.storage.

All data stored using web3.storage is made available for retrieval via [IPFS](https://ipfs.io/), the InterPlanetary File System. IPFS is a distributed, peer-to-peer network for storing and sharing content-addressed data. This guide shows you several ways to retrieve your data from IPFS:

- In your browser using an [HTTP gateway](https://web3.storage/docs/how-tos/retrieve/#using-an-ipfs-http-gateway).
- Using the Saturn dCDN.
- In your terminal using the [IPFS command-line tools](https://web3.storage/docs/how-tos/retrieve/#using-the-ipfs-command-line).
- In your terminal using [curl or Powershell](https://web3.storage/docs/how-tos/retrieve/#using-curl-or-powershell).

When retrieving any data, you'll be using the content CID of the upload (prefixed by `bafy…`).

**Using an IPFS HTTP gateway**

You can easily fetch any data stored using web3.storage using an IPFS HTTP gateway. Because IPFS is a peer-to-peer, decentralized network, you can use any public HTTP gateway to fetch your data. In this guide, we'll use the gateway at w3s.link (which is optimized for data stored with web3.storage), but you can see more worldwide gateways on the [IPFS Public Gateway Checker](https://ipfs.github.io/public-gateway-checker/).

You can use an IPFS gateway to view a list of all the files in that directory from your browser. To do so, simply create a gateway URL. For example, if your CID is bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu, you can make a URL for the w3s.link gateway as follows: `https://bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu.ipfs.w3s.link/`. Follow that link, and you'll see a page similar to this:

![](RackMultipart20231107-1-k3fcf9_html_5bb9fefc33b3be31.png)

If you want to link directly to a file within that directory, just add the file path after the CID portion of the link. For example: [bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu.ipfs.w3s.link/not-distributed.jpg](https://bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu.ipfs.w3s.link/not-distributed.jpg) could be used as a shareable link for your new favorite wallpaper.

**Tip**

Your web3.storage console page includes IPFS gateway links to all the content you've uploaded.

### [Setting the filename for downloads via gateways](https://web3.storage/docs/how-tos/retrieve/#setting-the-filename-for-downloads-via-gateways)

When downloading files from an HTTP gateway, web browsers will set the default filename for the downloaded file based on the path component of the gateway link. For example, if you use your browser's "Save link as..." feature on the following link, it should prompt you to save a file named treehouse.jpeg:

[https://bafybeicfnbaeigdtklwkrj35r4wtfppix732zromsadvgiu33mowah74yq.ipfs.w3s.link/treehouse.jpeg](https://bafybeicfnbaeigdtklwkrj35r4wtfppix732zromsadvgiu33mowah74yq.ipfs.w3s.link/treehouse.jpeg)

In the link above, the CID bafybeicfnbaeigdtklwkrj35r4wtfppix732zromsadvgiu33mowah74yq points to an IPFS directory listing, which maps from the filename treehouse.jpeg to the CID for the image itself.

Since the web3.storage client wraps your uploaded files in a directory by default, this is the most common kind of gateway link you're likely to need, and your users should get nice filenames when they download their content.

However, the behavior is a bit different if you make a gateway link directly to the image CID:

- [https://bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei.ipfs.w3s.link/](https://bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei.ipfs.w3s.link/)
- [https://ipfs.io/ipfs/bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei](https://ipfs.io/ipfs/bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei)

Both of the URLs above link directly to the CID of the image, without an associated filename. The first URL uses the recommended "subdomain" URL format for gateway links, while the second form uses a "path prefix" format that you may see in use elsewhere in the IPFS ecosystem.

Depending on which style of link you use, your browser will prompt you to save a file with a generic name like download, or with the CID as the filename.

If you have such a link, you can override the default filename by adding a query string parameter to your link of the form ?filename=\<desired-filename\>. For example, the following link will save as treehouse.jpeg, even though it links directly to the image by CID:

[https://bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei.ipfs.w3s.link/?filename=treehouse.jpeg](https://bafkreifvallbyfxnedeseuvkkswt5u3hbdb2fexcygbyjqy5a5rzmhrzei.ipfs.w3s.link/?filename=treehouse.jpeg)

**Other gateway endpoints**

Graph API, CAR fetching…

## [Using the IPFS command line](https://web3.storage/docs/how-tos/retrieve/#using-the-ipfs-command-line)

If you have the [IPFS command line interface](https://docs.ipfs.io/how-to/command-line-quick-start/) installed, you can use it directly to fetch data without going through a gateway. This also works if you've installed [IPFS Desktop](https://docs.ipfs.io/install/ipfs-desktop/), which includes the IPFS CLI.

To get the whole bundle and save it to a directory, run the following command:

```
ipfs get bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu
```

If you want to get a specific file out of the bundle, add its name onto the end of the ipfs get bafybie... command:

```
ipfs get bafybeidd2gyhagleh47qeg77xqndy2qy3yzn4vkxmk775bg2t5lpuy7pcu/youareanonsense.jpg
```

## [Using curl or Powershell](https://web3.storage/docs/how-tos/retrieve/#using-curl-or-powershell)

Sometimes you may need to just download a specific file to your computer using the command line. Unix-based operating systems, like Linux and macOS, can use curl. Windows users can use Powershell.

- Linux
- macOS
- Windows

1. Open a terminal window.
2. Use curl to download your file:

```
curl https://\<YOURCID\>.ipfs.w3s.link/\<FILENAME\>-o~/\<OUTPUTFILE\>
```

1. 
Replace \<YOUR CID\>, \<FILE NAME\>, and \<OUTPUT FILE\> with their respective values.
 | Variable | Replace with | Example | | --- | --- | --- | | \<YOUR CID\> | The CID of the file you want to download. | bafybeie2bjap32zi2yqh5jmpve5njwulnkualcbiszvwfu36jzjyqskceq | | \<FILE NAME\> | The _name_ of the file that you originally uploaded to web3.storage. | example.txt | | \<OUTPUT FILE\> | The path and filename that you want curl to save the file to. This can be different to \<FILE NAME\>. | Desktop/output-file.txt |
 Your complete command should look something like this:

```
curl https://bafybeie2bjap32zi2yqh5jmpve5njwulnkualcbiszvwfu36jzjyqskceq.ipfs.w3s.link/example.txt-o~/output-file.txt
```

## Next steps

Next, you'll learn about how to [list](https://web3.storage/docs/how-tos/list/)