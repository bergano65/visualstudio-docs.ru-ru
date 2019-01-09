---
title: 'IScriptNode:: CreateChildEntry | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a8ca4ab504a9da2a63d5c70330d50e2c97e09817
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088235"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Добавляет дочерний экземпляр `IScriptEntry`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `isn`  
 [in] Индекс дочернего элемента в родительском объекте.  
  
 `dwCookie`  
 [in] Значение определяется приложением, используется для связывания с объектом главного дочерний элемент.  
  
 `pszDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Для синтаксического анализа, узел обычно использует разделитель (например, две одинарные кавычки), чтобы обнаружить завершение блока скрипта.  
  
 Разделитель позволяет сценарию разработки ядра для предоставления предварительной обработки. Например ядро может заменить одинарной кавычки двумя одинарными кавычками для использования в качестве разделителя. Модуль определяет, как используется разделитель.  
  
 Значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс дочернего экземпляра.  
  
 Для `IScriptNode` объекты, представляющие веб-страницы, этот параметр возвращает `IScriptEntry` , который определяет блок сценария.  
  
 Для `IScriptEntry` объекты, представляющие блок сценария, этот параметр возвращает `IScriptEntry` , который определяет объект-функцию.  
  
 Для `IScriptEntry` объекта объекты, представляющие функции, этот метод завершается ошибкой.  
  
 Для `IScriptScriptlet` объектов, этот метод завершается ошибкой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `IScriptNode` Интерфейс представляет веб-страницы или его элементов. `IScriptEntry` Интерфейс (который является производным от `IScriptNode`) представляет блок сценария или объекта функции. `IScriptScriptlet` Интерфейс (который является производным от `IScriptEntry`) представляет обработчик событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)