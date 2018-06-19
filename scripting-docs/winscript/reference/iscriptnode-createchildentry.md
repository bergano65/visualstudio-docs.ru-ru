---
title: 'IScriptNode:: CreateChildEntry | Документы Microsoft'
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
ms.openlocfilehash: 8fcc010efe8fcf30a8f467dd94befff54bc5fac5
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
ms.locfileid: "24729694"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode::CreateChildEntry
Добавляет дочерний экземпляр `IScriptEntry`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Значение, определенное приложением используется для связи с объектом узла дочерний элемент.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Для синтаксического анализа, узел обычно использует разделитель (например, две одинарных кавычки), для определения конца блока скрипта.  
  
 Разделитель, который позволяет помещать скрипт создания ядром предварительной обработки. Например подсистема может заменить одинарную кавычку две одинарные кавычки для использования в качестве разделителя. Обработчик определяет, как используется разделитель.  
  
 Значение NULL, если разделитель не отмечает конец блока скрипта.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс дочернего экземпляра.  
  
 Для `IScriptNode` объекты, представляющие веб-страницы, этот параметр возвращает `IScriptEntry` , который определяет блок сценария.  
  
 Для `IScriptEntry` объекты, представляющие блок сценария, этот параметр возвращает `IScriptEntry` , который определяет объект функции.  
  
 Для `IScriptEntry` объекта объекты, представляющие функции, этот метод завершается ошибкой.  
  
 Для `IScriptScriptlet` объектов, этот метод завершается ошибкой.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 `IScriptNode` Интерфейс представляет веб-странице или в его элементах. `IScriptEntry` Интерфейс (который является производным от `IScriptNode`) представляет собой блок сценария или объекта функции. `IScriptScriptlet` Интерфейс (который является производным от `IScriptEntry`) представляет обработчик событий.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)