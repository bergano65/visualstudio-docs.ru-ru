---
title: "IDiaSession::findAcceleratorInlineesByName | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: "3"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25aceb146aac7d23647172e53989d30bd9d72a08
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
Возвращает перечисление символы для встроенные рамки, соответствующий имени заданной встроенной функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `name`  
 [in] Имя функции встроенного кода для поиска.  
  
 `option`  
 [in] Параметры поиска имени, используемый при поиске встроенного кадры, соответствуют `name`. Дополнительные сведения см. в разделе [NameSearchOptions-перечисление](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 [out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Эта функция осуществляет поиск inlinees только внутри функции-заглушки сочетаний клавиш. Пропускает записи процедура собственного C++.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)