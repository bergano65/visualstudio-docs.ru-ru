---
title: Команда Watch | Microsoft Docs
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
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9b1d5a1a1ffac1c67b5a3a1e1ad4a860c6b2ad4f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214361"
---
# <a name="watch-command"></a>Команда Watch
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Создает и открывает указанный экземпляр окна **Контрольное значение** . Окно **Контрольные значения** можно использовать для вычисления значений переменных, выражений и регистров, чтобы изменять эти значения и сохранять результаты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Аргументы  
 `index`  
 Обязательно. Номер экземпляра окна контрольных значений  
  
## <a name="remarks"></a>Примечания  
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>См. также  
 [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)   
 [Практическое: изменение значения в окне переменной](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Практическое: используйте диалоговое окно "Быстрая проверка"](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



