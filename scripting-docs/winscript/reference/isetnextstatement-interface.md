---
title: "Интерфейс ISetNextStatement | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: b570c2e0-a173-4f14-97d8-f39465753115
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bdd71a427a8ef2c57684eef75a044d0cedf42415
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="isetnextstatement-interface"></a>Интерфейс ISetNextStatement
Этот интерфейс реализуется интерпретатор разрешающее диспетчер отладки процессов обновить текущую инструкцию. Он реализован в кадр стека и PDM получает этого интерфейса через QueryInterface.  
  
 интерфейс предоставляет методы, которые полезны для настройки точки выполнения, который определяет следующий оператор для выполнения.  
  
 Помимо методов, наследуемых от `IUnknown`, `ISetNextStatement` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[ISetNextStatement::CanSetNextStatement](../../winscript/reference/isetnextstatement-cansetnextstatement.md)|Определяет, можно ли задать точку выполнения в указанное расположение.|  
|[ISetNextStatement::SetNextStatement](../../winscript/reference/isetnextstatement-setnextstatement.md)|Установка точки выполнения в указанное расположение.|