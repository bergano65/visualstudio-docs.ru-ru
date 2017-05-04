---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
Сведения о типе возвращений для объекта функции `IScriptEntry`.  
  
## Синтаксис  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### Параметры  
 `ppti`  
 \[out\] данные о типе, связанная с этим объектом функции `IScriptEntry`.  
  
 `piMethod`  
 \[out\] индекс метода в объекте `ITypeInfo`.  
  
## Возвращаемое значение  
 Объект `HRESULT`.  Допустимые значения включают, но не ограничиваются см. в следующей таблице.  
  
|Значение|Описание|  
|--------------|--------------|  
|`S_OK`|Метод успешно выполнен.|  
  
## Заметки  
 Вы сведения о типе набора с помощью [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) или [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Сведения о типе может быть сформирована запись, основанной на внутреннем представлении функции.  
  
## См. также  
 [Интерфейс IScriptEntry](../../winscript/reference/iscriptentry-interface.md)