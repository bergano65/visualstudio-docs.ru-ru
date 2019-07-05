---
title: Интерфейс ISetNextStatement | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: de300a7af8492e6431f6b8513cde84a15895ad96
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786312"
---
# <a name="isetnextstatement-interface"></a>Интерфейс ISetNextStatement
Этот интерфейс реализуется интерпретатор, чтобы разрешить диспетчер отладки процессов обновить текущую инструкцию. Он реализован в объект кадра стека, и PDM получает этот интерфейс, через QueryInterface.  
  
 интерфейс предоставляет методы, которые полезны для настройки точки выполнения, который определяет следующий оператор, который будет выполнен.  
  
 Помимо методов, наследуемых от `IUnknown`, `ISetNextStatement` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Определяет, можно ли установить точку выполнения в указанное расположение.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Установка точки выполнения в указанное расположение.|