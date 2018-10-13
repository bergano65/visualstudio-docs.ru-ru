---
title: Команда "Вывести исходный код" | Документы Майкрософт
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
- Debug.ListSource
helpviewer_keywords:
- Debug.ListSource command
- list source command
- ListSource command
ms.assetid: e45f08d2-f4a3-49c3-9452-aa60508e2f74
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ff216ddd8943ea971669c6ebb1c7c0306b02160f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49171981"
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
 Необязательный. Указание числа строк для отображения.  
  
 /Current  
 Необязательный. Отображение текущей строки.  
  
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



