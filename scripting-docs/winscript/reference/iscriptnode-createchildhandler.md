---
title: "IScriptNode::CreateChildHandler | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ff2ba40d1570e23f0256bd34ca8aff0f8d77ce5c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Добавляет в качестве экземпляра дочернего пользователи `IScriptNode`.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
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
 [in] Адрес по умолчанию имя, связанное с помощью сценариев.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] список идентификаторов из полное доменное имя узла.  
  
 `cpszNames`  
 [in] Количество идентификаторов в `prgpszNames` параметра.  
  
 `pszEvent`  
 [in] Адрес буфера, который определяет имя события, связанные с сценариев.  
  
 `pszDelimiter`  
 [in] Адрес разделитель end из скрипта блока. Для синтаксического анализа, узел обычно использует разделитель (например, две одинарных кавычки), для определения конца блока скрипта.  
  
 Разделитель, который позволяет предварительной обработки для сценария создания обработчика. Например подсистема может заменить одинарную кавычку две одинарные кавычки для использования в качестве разделителя. Обработчик определяет, как используется разделитель.  
  
 Значение NULL, если разделитель не используется для обозначения конца блока скрипта.  
  
 `ptiSignature`  
 [in] Сведения о типе для объекта функции.  
  
 `iMethodSignature`  
 [in] Индекс функции в `ITypeInfo``ptiSignature` параметра.  
  
 `isn`  
 [in] Индекс дочернего элемента в родительском объекте.  
  
 `dwCookie`  
 [in] Определяемые приложением значения, используемый для связи с объектом узла запись.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс дочернего экземпляра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Пользователи указывает обработчик событий. Этот метод создает пользователи, если она вызвана `IScriptNode` , представляющий веб-страницы. Этот метод завершается неудачно, если она вызвана других интерфейсов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)