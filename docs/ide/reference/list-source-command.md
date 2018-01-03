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
ms.workload: multiple
ms.openlocfilehash: bb3f3e6cb441697fb8546fcec485d292e979690b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
 Необязательный. Указание числа строк для отображения.  
  
 /Current  
 Необязательно. Отображение текущей строки.  
  
 /File:`filename`  
 Необязательный. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.  
  
 /Line:`number`  
 Необязательный. Отображение определенного номера строки.  
  
 /ShowLineNumbers:`yes|no`  
 Необязательный. Указание отображения номеров строк.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)