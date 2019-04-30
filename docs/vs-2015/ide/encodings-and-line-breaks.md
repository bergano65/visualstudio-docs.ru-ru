---
title: Кодировки и разрывы строк | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 6ceec5e44ade219f069e72f712129a137d70875f
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437526"
---
# <a name="encodings-and-line-breaks"></a>Кодировки и разрывы строк
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В Visual Studio можно использовать параметры в разделе **Файл > Дополнительные параметры сохранения**, чтобы определить тип символов разрыва строки. Кроме того, с помощью этих параметров можно изменить кодировку файла.  
  
> [!NOTE]
> При наличии определенных типов параметров разработки (Visual Basic, F#, веб-разработки) пункт **Дополнительные параметры сохранения** может не отображаться в меню. Чтобы изменить параметры (например, "Общие"), перейдите в раздел меню **Сервис > Импорт и экспорт параметров**. Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 В Visual Studio следующие символы интерпретируются как разрывы строк:  
  
- CRLF: возврат каретки + перевод строки, символы Юникода 000D + 000A  
  
- LF: перевод строки, символ Юникода 000A  
  
- NEL: следующая строка, символ Юникода 0085  
  
- LS: разделитель строки, символ Юникода 2028  
  
- PS: разделитель абзаца, символ Юникода 2029  
  
  Для текста, который копируется из других приложений, сохраняется исходная кодировка и символы разрыва строки. Например, при копировании текста из Блокнота и вставке его в текстовый файл в Visual Studio текст имеет те же параметры, которые применялись в Блокноте.  
  
  При открытии файла, который содержит разные символы разрыва строки, может появиться диалоговое окно с запросом о том, следует ли нормализовать несогласованные символы разрыва строки и какой тип разрыва строки выбрать.
