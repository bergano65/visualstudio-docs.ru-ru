---
title: IScriptNode::CreateChildHandler | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2ef4c9318cb13459ab787878218bf7ca68052f29
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094189"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Добавляет в качестве дочернего экземпляра пользователи `IScriptNode`.  
  
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
 [in] Адрес по умолчанию имя для связи со скриптлетом.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] список идентификаторов из полного имени на узле.  
  
 `cpszNames`  
 [in] Число идентификаторов в `prgpszNames` параметра.  
  
 `pszEvent`  
 [in] Адрес буфера, который определяет имя события, связанные со скриптлетом.  
  
 `pszDelimiter`  
 [in] Адрес-объекта блок сценариев end разделитель. Для синтаксического анализа, узел обычно использует разделитель (например, две одинарные кавычки), чтобы обнаружить завершение блока скрипта.  
  
 Разделитель позволяет предварительной обработки с помощью сценария создания ядра. Например ядро может заменить одинарной кавычки двумя одинарными кавычками для использования в качестве разделителя. Модуль определяет, как используется разделитель.  
  
 Значение NULL, если разделитель не используется для обозначения конца блока скрипта.  
  
 `ptiSignature`  
 [in] Сведения о типе для объекта функции.  
  
 `iMethodSignature`  
 [in] Индекс функции в `ITypeInfo``ptiSignature` параметра.  
  
 `isn`  
 [in] Индекс дочернего элемента в родительском объекте.  
  
 `dwCookie`  
 [in] Определяемый приложением значение, используемое должен быть сопоставлен объект узла операции.  
  
 `ppse`  
 [out] Адрес переменной, которая получает указатель на `IScriptEntry` интерфейс дочернего экземпляра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
 Пользователи указывает обработчик событий. Этот метод создает пользователи, если она вызвана `IScriptNode` , представляющий веб-страницы. Этот метод завершается неудачно, если вызывается с помощью других интерфейсов.  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IScriptNode](../../winscript/reference/iscriptnode-interface.md)   
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)