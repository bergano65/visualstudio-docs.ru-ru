---
title: 'Практическое: отладка машинных библиотек DLL | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2807fa9d0085c70e3336a5f9a0d66b28a775f4fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49830604"
---
# <a name="how-to-debug-native-dlls"></a>Практическое руководство. Отладка машинных библиотек DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, в меню "Сервис" выберите команду "Импорт и экспорт параметров". Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Отладку библиотеки DLL можно начинать с одного из следующих вариантов:  
  
- С проекта, используемого для создания исполняемого файла, который вызывает библиотеку DLL.  
  
  \- или -  
  
- С проекта, используемого для создания самой библиотеки DLL.  
  
  Если имеется проект, используемый для создания исполняемого файла, отладку следует начать с этого проекта. Затем можно открыть исходный файл библиотеки DLL и задать в нем точки останова, даже если он не является частью проекта, использованного для создания исполняемого файла. Дополнительные сведения см. в разделе [точки останова](http://msdn.microsoft.com/en-us/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Если отладка начинается с проекта, создающего библиотеку DLL, необходимо задать исполняемый файл, который будет использоваться при отладке данной DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Задание исполняемого файла для сеанса отладки  
  
1. В **обозревателе решений**, выберите проект, который создает библиотеку DLL.  
  
2. Из **представление** меню, выберите**страницы свойств**.  
  
3. В **страницы свойств** , открытом окне **свойства конфигурации** папку и выберите **Отладка** категории.  
  
4. В **команда** укажите путь к контейнеру. Например: C:\Program Files\MyApplication\MYAPP.EXE.  
  
5. В **аргументы команды** укажите необходимые аргументы для исполняемого файла.  
  
   Если вы не укажете исполняемый файл в _проекта_**страницы свойств** диалоговом окне [исполняемый файл для отладки-диалоговое окно сеанса](../debugger/executable-for-debugging-session-dialog-box.md) отображается при запуске отладки.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка в Visual Studio](../debugger/debugging-in-visual-studio.md)



