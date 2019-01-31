---
title: Команда Watch | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b1a04dce73dbf2551b51f2395b3512e62daf3766
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54788194"
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
 Обязательный. Номер экземпляра окна контрольных значений  
  
## <a name="remarks"></a>Примечания  
 Значение `index` должно быть целым числом. Допустимые значения: 1, 2, 3 и 4.  
  
## <a name="example"></a>Пример  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Окна "Видимые" и "Локальные"](../../debugger/autos-and-locals-windows.md)   
 [Практическое руководство. Изменение значения в окне переменной](http://msdn.microsoft.com/library/36f464ab-c900-4c0b-9ab3-557b3d9cdab5)   
 [Практическое руководство. Используйте диалоговое окно "Быстрая проверка"](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Команды Visual Studio](../../ide/reference/visual-studio-commands.md)   
 [Командное окно](../../ide/reference/command-window.md)   
 [Поле "Поиск/Команда"](../../ide/find-command-box.md)   
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
