---
title: 'IActiveScript:: Clone | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575801"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Копирует текущий обработчик скриптов (за исключением любого текущего состояния выполнения), возвращая загруженный обработчик скриптов, не имеющий сайта в текущем потоке. Свойства этого нового обработчика скриптов будут совпадать со свойствами, в которых будет находиться исходный обработчик скриптов, если он был переведен в инициализированное состояние.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppscript`  
 заполняет Адрес переменной, которая получает указатель на интерфейс [IActiveScript](../../winscript/reference/iactivescript.md) клонированного обработчика скриптов. Узел должен создать сайт и вызвать метод [IActiveScript:: сетскриптсите](../../winscript/reference/iactivescript-setscriptsite.md) нового обработчика скриптов, прежде чем он будет находиться в инициализированном состоянии и, следовательно, использовать его.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает одно из следующих значений:  
  
|Возвращаемое значение|Смысл|  
|------------------|-------------|  
|`S_OK`|Выполнено.|  
|`E_NOTIMPL`|Этот метод не поддерживается.|  
|`E_POINTER`|Указан недопустимый указатель.|  
|`E_UNEXPECTED`|Вызов не ожидался (например, обработчик скриптов еще не загружен или не инициализирован).|  
  
## <a name="remarks"></a>Заметки  
 Метод `IActiveScript::Clone` является оптимизацией `IPersist*::Save`, `CoCreateInstance` и `IPersist*::Load`, поэтому состояние нового обработчика скриптов должно быть таким же, как если бы исходное состояние обработчика скриптов сохранялось и загружалось в новый обработчик скриптов. Именованные элементы дублируются в клонированном обработчике скриптов, но определенные указатели на объекты для каждого элемента заменяются и получаются с помощью метода [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . Это позволяет использовать идентичную объектную модель с точками входа для отдельных потоков (модель подразделений).  
  
 Этот метод используется для многопоточных серверных узлов, которые могут запускать несколько экземпляров одного и того же скрипта. Обработчик скриптов может возвращать `E_NOTIMPL`. в этом случае узел может добиться того же результата путем дублирования постоянного состояния и создания нового экземпляра обработчика сценариев с интерфейсом `IPersist*`.  
  
 Этот метод может быть вызван из не базовых потоков, что приводит к небазовому вызову для размещения объектов или интерфейсу [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>См. также  
 [IActiveScript](../../winscript/reference/iactivescript.md)