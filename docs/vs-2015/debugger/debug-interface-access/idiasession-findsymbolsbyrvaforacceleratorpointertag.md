---
title: IDiaSession::findSymbolsByRVAForAcceleratorPointerTag | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
ms.assetid: a073cc45-0c7b-417e-b5fc-a3b08beccdbc
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b51c1e8e85d1a9b58faa9d15b74d2dff71ef3f33
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220733"
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



