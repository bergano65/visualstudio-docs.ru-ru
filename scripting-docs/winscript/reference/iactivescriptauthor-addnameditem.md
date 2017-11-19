---
title: "IActiveScriptAuthor::AddNamedItem | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScriptAuthor.AddNamedItem
apilocation: scrobj.dll
helpviewer_keywords: IActiveScriptAuthor::AddNamedItem
ms.assetid: 951003b6-1c4a-4086-b7ce-2f128e007280
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 83d2597f8468bb97d20da655a56a751191ec4b55
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddnameditem"></a>IActiveScriptAuthor::AddNamedItem
Добавляет имя элемента на корневом уровне скрипт создания механизма пространства имен. Объект *корневой элемент* — это объект, содержащую свойства и методы, а также может содержать источник события.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
HRESULT AddNamedItem(  
   LPCOLESTR          pszName,  
   DWORD              dwFlags,  
   IDispatch          *pdisp  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pszName`  
 [in] Имя элемента, как видно из скрипта. Имя должно быть уникальным и является сохраняемым.  
  
 `dwFlags`  
 [in] Флаги, связанные с именованным элементом. Может быть сочетанием следующих значений:  
  
|Константа|Значение|Описание|  
|--------------|-----------|-----------------|  
|SCRIPTITEM_ISVISIBLE|0x00000002|Указывает, доступны в пространстве имен сценарий, имя элемента. Это обеспечивает доступ к элемента свойства, методы и события.<br /><br /> По соглашению свойства элемента включают дочерних элементов данного элемента. Таким образом все свойства дочерних элементов объекта и методы (и их дочерних элементов, рекурсивно) доступны.|  
|SCRIPTITEM_ISSOURCE|0x00000004|Указывает источник элемента события, скрипт может иметь обработчики событий в скрипт.|  
|SCRIPTITEM_GLOBALMEMBERS|0x00000008|Указывает, что элемент является коллекции глобальных свойств и методов, связанных со сценарием. Его члены создаются как глобальные переменные и методы.|  
|SCRIPTITEM_ISPERSISTENT|0x00000040|Указывает, что сохранения элемента при разработки engine сценарий сохранен.|  
|SCRIPTITEM_CODEONLY|0x00000200|Указывает, что именованный элемент представляет объект только в коде и не имеет члена для разработки.|  
|SCRIPTITEM_NOCODE|0x00000400|Указывает, что именованный элемент только имя добавляемого и никак автору.|  
  
 `pdisp`  
 [in] `IDispatch` Из `NamedItem` объект, используемый для сбора, методы, свойства или источника события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Объект `HRESULT`. Допустимые значения включают, но не ограничиваются, значения, приведенные в следующей таблице.  
  
|Значение|Описание|  
|-----------|-----------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Интерфейс IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::RemoveNamedItem](../../winscript/reference/iactivescriptauthor-removenameditem.md)