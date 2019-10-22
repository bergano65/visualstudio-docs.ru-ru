---
title: 'Искриптноде:: Креатечилдентри | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573614"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
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
 окне Индекс дочернего элемента в родительском элементе.  
  
 `dwCookie`  
 окне Определяемое приложением значение, используемое для связывания дочерней записи с объектом узла.  
  
 `pszDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Для синтаксического анализа хост обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца блока скрипта.  
  
 Разделитель позволяет подсистеме создания скриптов обеспечить предварительную обработку. Например, подсистема может заменить одинарную кавычку двумя одинарными кавычками для использования в качестве разделителя. Механизм определяет, как используется разделитель.  
  
 Задайте значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `ppse`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IScriptEntry` дочернего экземпляра.  
  
 Для `IScriptNode` объектов, представляющих веб-страницу, этот параметр возвращает экземпляр `IScriptEntry`, указывающий блок скрипта.  
  
 Для `IScriptEntry` объектов, представляющих блок скрипта, этот параметр возвращает экземпляр `IScriptEntry`, указывающий объект функции.  
  
 Для `IScriptEntry` объектов, представляющих объект функции, этот метод завершается ошибкой.  
  
 Для `IScriptScriptlet` объектов этот метод завершается ошибкой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Интерфейс `IScriptNode` представляет веб-страницу или ее элементы. Интерфейс `IScriptEntry` (производный от `IScriptNode`) представляет либо блок скрипта, либо объект функции. Интерфейс `IScriptScriptlet` (производный от `IScriptEntry`) представляет обработчик событий.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса искриптноде](../../winscript/reference/iscriptnode-interface.md)  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)