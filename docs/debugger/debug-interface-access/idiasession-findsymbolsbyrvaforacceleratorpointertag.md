---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 672c3a209758342aa28fa7382c02e03b01ece540
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
Задано значение соответствующего тега, этот метод возвращает перечисление символов, содержащихся в функции заглушки сочетаний клавиш указанного родительского объекта в указанный относительный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] `IDiaSymbol` , Соответствующего функции заглушки сочетаний клавиш для поиска.  
  
 `tagValue`  
 [in] Значение тега указателя.  
  
 `rva`  
 [in] Относительный виртуальный адрес.  
  
 `ppResult`  
 [out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается только в `IDiaSymbol` интерфейс, который соответствует функции заглушки сочетаний клавиш.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)