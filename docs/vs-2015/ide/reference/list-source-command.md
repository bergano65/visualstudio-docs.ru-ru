---
title: Команда "Вывести исходный код" | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: e0a4a8482dc1c2c66a45902f2f3382b179b46b13
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199128"
---
# <a name="list-source-command"></a>Команда List Source
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Отображает заданные строки исходного кода.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.ListSource [/Count:number] [/Current] [/File:filename]  
[/Line:number] [/ShowLineNumbers:yes|no]  
```  
  
## <a name="switches"></a>Переключатели  
 /Count:`number`  
 Необязательный параметр. Указание числа строк для отображения.  
  
 /Current  
 Необязательный параметр. Отображение текущей строки.  
  
 /File:`filename`  
 Необязательный параметр. Путь к файлу для отображения. Если имя файла не указано, при выполнении команды выводится исходный код строки текущего оператора.  
  
 /Line:`number`  
 Необязательный параметр. Отображение определенного номера строки.  
  
 /ShowLineNumbers:`yes|no`  
 Необязательный параметр. Указание отображения номеров строк.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="example"></a>Пример  
 В приведенном ниже примере показан исходный код со строки 4 файла Form1.vb с отображением номеров строк.  
  
```  
Debug.ListSource /File:"C:\Visual Studio Projects\Form1.vb" /Line:4 /ShowLineNumbers:yes  
```  
  
## <a name="see-also"></a>См. также  
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)
