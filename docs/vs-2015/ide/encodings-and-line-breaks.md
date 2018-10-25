---
title: Кодировки и разрывы строк | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.Encoding
helpviewer_keywords:
- line breaks
- encoding
- Visual Studio, encoding
- editors, line breaks
- line break characters
- Visual Studio, line break characters
ms.assetid: 8f9b3ffc-7b8d-44f4-87cb-dc29105be12d
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 17deca1afc78e238e098285e760a791504b61fe8
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880732"
---
# <a name="encodings-and-line-breaks"></a>Кодировки и разрывы строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно использовать параметры в разделе **Файл > Дополнительные параметры сохранения**, чтобы определить тип символов разрыва строки. Кроме того, с помощью этих параметров можно изменить кодировку файла.  
  
> [!NOTE]
>  При наличии определенных типов параметров разработки (Visual Basic, F#, веб-разработки) пункт **Дополнительные параметры сохранения** может не отображаться в меню. Чтобы изменить параметры (например, "Общие"), перейдите в раздел меню **Сервис > Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 В Visual Studio следующие символы интерпретируются как разрывы строк:  
  
- CRLF: возврат каретки + перевод строки, символы Юникода 000D + 000A;  
  
- LF: перевод строки, символ Юникода 000A;  
  
- NEL: следующая строка, символ Юникода 0085;  
  
- LF: разделитель строки, символ Юникода 2028;  
  
- PS: разделитель абзаца, символ Юникода 2029.  
  
  Для текста, который копируется из других приложений, сохраняется исходная кодировка и символы разрыва строки. Например, при копировании текста из Блокнота и вставке его в текстовый файл в Visual Studio текст имеет те же параметры, которые применялись в Блокноте.  
  
  При открытии файла, который содержит разные символы разрыва строки, может появиться диалоговое окно с запросом о том, следует ли нормализовать несогласованные символы разрыва строки и какой тип разрыва строки выбрать.



