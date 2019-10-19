---
title: 'Иактивескриптаусор:: AddNamedItem | Документация Майкрософт'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddNamedItem
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: 19
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0d2f08a49fdc768e87152bf486ce48687c79e68
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577248"
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Добавляет имя элемента корневого уровня в пространство имен механизма разработки скриптов. *Элемент корневого уровня* — это объект, который может содержать свойства и методы, а также может содержать источник события.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 окне Имя элемента, отображаемое в скрипте. Имя должно быть уникальным и постоянным.  
  
 `dwFlags`  
 окне Флаги, связанные с именованным элементом. Может быть сочетанием следующих значений:  
  
|Константа|значения|Описание|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Указывает, что имя элемента доступно в пространстве имен скрипта. Это позволяет получить доступ к свойствам, методам и событиям элемента.<br /><br /> По соглашению свойства элемента включают дочерние элементы элемента. Таким образом, все свойства и методы дочернего объекта (и их дочерние элементы, рекурсивно) становятся доступными.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Указывает события источника элемента, которые скрипт может иметь обработчики событий скрипта.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Указывает, что элемент является коллекцией глобальных свойств и методов, связанных с скриптом. Его члены создаются как глобальные переменные и методы.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Указывает, что элемент должен быть сохранен при сохранении обработчика создания скриптов.|  
|SCRIPTITEM_CODEONLY|0x00000200|Указывает, что именованный элемент представляет объект только для кода и не имеет члена для создания.|  
|SCRIPTITEM_NOCODE|0x00000400|Указывает, что именованный элемент является только добавляемым именем и не имеет ничего автора.|  
  
 `pdisp`  
 окне @No__t_0 объекта `NamedItem`, который используется для получения сведений о методах, свойствах или источнике события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|значения|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Заметки  
  
## <a name="see-also"></a>См. также  
 @No__t_1 [интерфейса иактивескриптаусор](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)