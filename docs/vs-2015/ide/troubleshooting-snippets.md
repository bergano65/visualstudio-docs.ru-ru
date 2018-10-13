---
title: Устранение неполадок, связанных с использованием фрагментов | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IntelliSense Code Snippets, troubleshooting
- troubleshooting IntelliSense Code Snippets
- troubleshooting Visual Basic, IntelliSense Code Snippets
ms.assetid: 7b6dd40e-2f78-4b50-8e68-41fac1bcb81e
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4fff2767c962cf6899840e54bff798bae1f9e202
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49304815"
---
# <a name="troubleshooting-snippets"></a>Устранение неполадок, связанных с использованием фрагментов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Проблемы с фрагментами кода IntelliSense обычно вызваны двумя причинами: поврежденный файл фрагмента или неправильное его содержимое.  
  
## <a name="common-problems"></a>Распространенные проблемы  
  
### <a name="the-snippet-cannot-be-dragged-from-file-explorer-to-a-visual-studio-source-file"></a>Не удается перетащить фрагмент кода из проводника в исходный файл Visual Studio  
  
-   Возможно, XML-код в файле фрагмента поврежден. **Редактор XML** в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет найти нарушения структуры XML.  
  
-   Возможно, файл фрагмента не соответствует схеме фрагмента. **Редактор XML** в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] позволяет найти нарушения структуры XML.  
  
### <a name="the-code-has-compiler-errors-that-are-not-highlighted"></a>В коде есть невыделенные ошибки компилятора  
  
-   Возможно, отсутствует ссылка на проект. Изучите документацию о фрагменте. Если ссылка на компьютере отсутствует, ее потребуется установить. Вставка фрагмента должна добавить в проект все необходимые ссылки. Если для фрагмента отсутствуют справочные сведения, об этой ошибке можно сообщить автору фрагмента.  
  
-   Возможно, не определена переменная. Неопределенные переменные во фрагменте кода должны быть выделены. В противном случае об этой ошибке можно сообщить автору фрагмента.  
  
## <a name="see-also"></a>См. также  
 [Фрагменты кода](../ide/code-snippets.md)



