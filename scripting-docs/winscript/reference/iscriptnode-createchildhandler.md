---
title: 'Искриптноде:: Креатечилдхандлер | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573602"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Добавляет скриптлет в качестве дочернего экземпляра `IScriptNode`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszDefaultName`  
 окне Адрес имени по умолчанию, связываемого с скриптлет.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Список идентификаторов из полного имени на узле.  
  
 `cpszNames`  
 окне Число идентификаторов в параметре `prgpszNames`.  
  
 `pszEvent`  
 окне Адрес буфера, определяющий имя события, связанное с скриптлет.  
  
 `pszDelimiter`  
 окне Адрес разделителя-блока конца скрипта. Для синтаксического анализа хост обычно использует разделитель (например, две одинарные кавычки) для обнаружения конца блока скрипта.  
  
 Разделитель включает предварительную обработку с помощью обработчика создания скриптов. Например, подсистема может заменить одинарную кавычку двумя одинарными кавычками для использования в качестве разделителя. Механизм определяет, как используется разделитель.  
  
 Задайте значение NULL, если для обнаружения конца блока скрипта не используется разделитель.  
  
 `ptiSignature`  
 окне Сведения о типе для объекта функции.  
  
 `iMethodSignature`  
 окне Индекс функции в параметре `ITypeInfo``ptiSignature`.  
  
 `isn`  
 окне Индекс дочернего элемента в родительском элементе.  
  
 `dwCookie`  
 окне Определяемое приложением значение, которое используется для связывания записи с объектом узла.  
  
 `ppse`  
 заполняет Адрес переменной, которая получает указатель на интерфейс `IScriptEntry` дочернего экземпляра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
 Скриптлет Указывает обработчик событий. Этот метод создает скриптлет, если он вызывается объектом `IScriptNode`, представляющим веб-страницу. Этот метод не выполняется, если он вызывается другими интерфейсами.  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса искриптноде](../../winscript/reference/iscriptnode-interface.md)  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)