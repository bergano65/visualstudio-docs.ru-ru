---
title: 'IDiaSymbol:: Финдсимболсбирвафоракцелераторпоинтертаг | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 024ccd78-5867-4ca7-bc26-548758e9ac53
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ee1aea023124fb8277fd13cf341a63fca92c37cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149865"
---
# <a name="idiasymbolfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При наличии соответствующего значения тега этот метод возвращает перечисление символов, содержащихся в этой функции-заглушке, по указанному относительному виртуальному адресу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT findSymbolsByRVAForAcceleratorPointerTag (   
   DWORD             tagValue,  
   DWORD             rva,  
   IDiaEnumSymbols** ppResult);  
```  
  
#### <a name="parameters"></a>Параметры  
 `tagValue`  
 окне Значение тега указателя, для которого обнаружены записи символов с точками.  
  
 `rva`  
 окне RVA, используемый для фильтрации символов, соответствующих переменной-Point с указанным значением тега.  
  
 `ppResult`  
 заполняет Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с помощью результата.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает `S_FALSE` или код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод следует вызывать только в `IDiaSymbol` интерфейсе, соответствующем функции-заглушке ускорителя.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
