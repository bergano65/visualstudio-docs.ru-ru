---
title: "Команда \"Вывести исходный код\" | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: "6"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2f94f7bea2f4742fa975948d838e0cb01ce5e11e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="list-source-command"></a>Команда List Source
Отображает заданные строки исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Переключатели  
 /Count:`number`  
 Необязательно. Указание числа строк для отображения.  
  
 /Current  
 Необязательно. Отображение текущей строки.  
  
 /File:`filename`  
 Необязательно. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.  
  
 /Line:`number`  
 Необязательно. Отображение определенного номера строки.  
  
 /ShowLineNumbers:`yes|no`  
 Необязательно. Указание отображения номеров строк.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)