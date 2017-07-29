---
title: "Кодировки и разрывы строк | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
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
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 34c400c280096acb7e0ce272fa717cbc2f8f0d8a
ms.contentlocale: ru-ru
ms.lasthandoff: 05/24/2017

---
# <a name="encodings-and-line-breaks"></a>Кодировки и разрывы строк
В Visual Studio можно использовать параметры в разделе **Файл > Дополнительные параметры сохранения**, чтобы определить тип символов разрыва строки. Кроме того, с помощью этих параметров можно изменить кодировку файла.  
  
> [!NOTE]
>  При наличии определенных типов параметров разработки (Visual Basic, F#, веб-разработки) пункт **Дополнительные параметры сохранения** может не отображаться в меню. Чтобы изменить параметры (например, "Общие"), перейдите в раздел меню **Сервис > Импорт и экспорт параметров**. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 В Visual Studio следующие символы интерпретируются как разрывы строк:  
  
-   CRLF: возврат каретки + перевод строки, символы Юникода 000D + 000A;  
  
-   LF: перевод строки, символ Юникода 000A;  
  
-   NEL: следующая строка, символ Юникода 0085;  
  
-   LF: разделитель строки, символ Юникода 2028;  
  
-   PS: разделитель абзаца, символ Юникода 2029.  
  
 Для текста, который копируется из других приложений, сохраняется исходная кодировка и символы разрыва строки. Например, при копировании текста из Блокнота и вставке его в текстовый файл в Visual Studio текст имеет те же параметры, которые применялись в Блокноте.  
  
 При открытии файла, который содержит разные символы разрыва строки, может появиться диалоговое окно с запросом о том, следует ли нормализовать несогласованные символы разрыва строки и какой тип разрыва строки выбрать.
