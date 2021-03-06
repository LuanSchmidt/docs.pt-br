---
title: Como carregar um arquivo
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345556"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a>Como carregar um arquivo no Visual Basic

O método <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> pode ser usado para carregar um arquivo e armazená-lo em um local remoto. Se o parâmetro `ShowUI` for definido como `True`, uma caixa de diálogo será exibida mostrando o andamento do upload e permitirá que os usuários cancelem a operação.  
  
### <a name="to-upload-a-file"></a>Para carregar um arquivo  
  
- Use o método `UploadFile` para carregar um arquivo, especificando o local do arquivo de origem e o local do diretório de destino como uma cadeia de caracteres ou URI (Uniform Resource Identifier). Este exemplo carrega o arquivo `Order.txt` para `http://www.cohowinery.com/uploads.aspx`.  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a>Para carregar um arquivo e mostrar o andamento da operação  
  
- Use o método `UploadFile` para carregar um arquivo, especificando o local do arquivo de origem e o local do diretório de destino como uma cadeia de caracteres ou URI. Este exemplo carrega o arquivo `Order.txt` para `http://www.cohowinery.com/uploads.aspx` sem fornecer um nome de usuário ou senha, mostra o andamento do upload e tem um intervalo de tempo limite de 500 milissegundos.  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a>Para carregar um arquivo, fornecendo um nome de usuário e senha  
  
- Use o método `UploadFile` para carregar um arquivo, especificando o local do arquivo de origem e o local do diretório de destino como uma cadeia de caracteres ou URI e especificando o nome de usuário e senha. Este exemplo carrega o arquivo `Order.txt` para `http://www.cohowinery.com/uploads.aspx`, fornecendo o nome de usuário `anonymous` e uma senha em branco.  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a>Programação Robusta  

 As seguintes condições podem lançar uma exceção:  
  
- O caminho do arquivo local não é válido (<xref:System.ArgumentException>).  
  
- Falha na autenticação (<xref:System.Security.SecurityException>).  
  
- A conexão ultrapassou o tempo limite (<xref:System.TimeoutException>).  
  
## <a name="see-also"></a>Consulte também

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [Como Baixar um Arquivo](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [Como analisar demarcadores de arquivo](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
