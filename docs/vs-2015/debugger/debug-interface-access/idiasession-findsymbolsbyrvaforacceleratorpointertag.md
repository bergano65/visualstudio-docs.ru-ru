---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0711c95310d4d3613d8b82bccbecab122bf19ef8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68196365"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Учитывая соответствующее значение тега, этот метод возвращает перечисление символы, которые содержатся в функции заглушки Accelerator указанного родительского объекта в указанный относительный виртуальный адрес.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   IDiaSymbol*           parent,  
   DWORD                 tagValue,  
   DWORD                 rva,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 [in] `IDiaSymbol` , Соответствующий функции заглушки сочетаний клавиш для поиска.  
  
 `tagValue`  
 [in] Указатель на значение тега.  
  
 `rva`  
 [in] Относительный виртуальный адрес.  
  
 `ppResult`  
 [out] Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с результатом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод следует вызывать только в `IDiaSymbol` интерфейс, который соответствует функции заглушки сочетаний клавиш.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
