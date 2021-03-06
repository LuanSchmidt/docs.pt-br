---
title: Como invocar o compilador de linha de comando
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line [Visual Basic], arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
ms.openlocfilehash: 3b34ebba68c9c9b2a8335822d0ffaef2a9b06d7c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344253"
---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Como invocar o compilador de linha de comando (Visual Basic)

Você pode invocar o compilador de linha de comando digitando o nome do seu arquivo executável na linha de comando, também conhecido como o prompt do MS-DOS. Se você compilar a partir do prompt de comando padrão do Windows, deverá digitar o caminho totalmente qualificado para o arquivo executável. Para substituir esse comportamento padrão, você pode usar o Prompt de Comando do Desenvolvedor para o Visual Studio ou modificar a variável de ambiente PATH. Ambos permitem que você compile a partir de qualquer diretório simplesmente digitando o nome do compilador.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-invoke-the-compiler-using-the-developer-command-prompt-for-visual-studio"></a>Para invocar o compilador usando o Prompt de Comando do Desenvolvedor para Visual Studio

1. Abra a pasta Ferramentas do Visual Studio Program dentro do grupo de programas Microsoft Visual Studio.

2. Você pode usar o Prompt de Comando do Desenvolvedor para que o Visual Studio acesse o compilador de qualquer diretório em seu computador, se o Visual Studio estiver instalado.

3. Invocar o Prompt de Comando do Desenvolvedor para o Visual Studio.

4. Na linha de comando, digite `vbc.exe` *sourceFileName* e pressione Enter.

    Por exemplo, se você armazenou o código-fonte em um diretório chamado `SourceFiles`, abra o prompt de comando e digite `cd SourceFiles` para alterar para esse diretório. Se o diretório contiver um arquivo de origem chamado `Source.vb`, você poderá compilá-lo digitando `vbc.exe Source.vb`.

## <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Para definir a variável de ambiente PATH para o compilador para o prompt de comando do Windows

1. Use o recurso de pesquisa do Windows para localizar o Vbc. exe no disco local.

    O nome exato do diretório em que o compilador está localizado depende do local do diretório do Windows e da versão do ".NET Framework" instalado. Se você tiver mais de uma versão do ".NET Framework" instalada, deverá determinar qual versão usar (normalmente a versão mais recente).

2. No menu **Iniciar** , clique com o botão direito do mouse em **meu computador**e, em seguida, clique em **Propriedades** no menu de atalho.

3. Clique na guia **Avançado** e em **Variáveis de Ambiente**.

4. No painel variáveis do **sistema** , selecione **caminho** na lista e clique em **Editar**.

5. Na caixa de diálogo Editar variável do **sistema** , mova o ponto de inserção para o final da cadeia de caracteres no campo **valor da variável** e digite um ponto e vírgula (;) seguido do nome completo do diretório encontrado na etapa 1.

6. Clique em **OK** para confirmar suas edições e fechar as caixas de diálogo.

     Depois de alterar a variável de ambiente PATH, você pode executar o compilador Visual Basic no prompt de comando do Windows de qualquer diretório no computador.

## <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Para invocar o compilador usando o prompt de comando do Windows

1. No menu **Iniciar** , clique na pasta **acessórios** e, em seguida, abra o **prompt de comando do Windows**.

2. Na linha de comando, digite `vbc.exe`*sourceFileName* e pressione Enter.

     Por exemplo, se você armazenou o código-fonte em um diretório chamado `SourceFiles`, abra o prompt de comando e digite `cd SourceFiles` para alterar para esse diretório. Se o diretório contiver um arquivo de origem chamado `Source.vb`, você poderá compilá-lo digitando `vbc.exe Source.vb`.

## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Compilação Condicional](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
