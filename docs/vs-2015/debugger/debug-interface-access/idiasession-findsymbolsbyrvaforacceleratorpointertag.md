---
title: 'IDiaSession:: Финдсимболсбирвафоракцелераторпоинтертаг | Документация Майкрософт'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196365"
---
# <a name="idiasessionfindsymbolsbyrvaforacceleratorpointertag"></a>IDiaSession::findSymbolsByRVAForAcceleratorPointerTag
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

При наличии соответствующего значения тега этот метод возвращает перечисление символов, содержащихся в указанной родительской функции-заглушке ускорителя, по указанному относительному виртуальному адресу.  
  
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
 окне Объект `IDiaSymbol` , соответствующий функции-заглушке ускорителя для поиска.  
  
 `tagValue`  
 окне Значение тега указателя.  
  
 `rva`  
 окне Относительный виртуальный адрес.  
  
 `ppResult`  
 заполняет Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с помощью результата.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод следует вызывать только в `IDiaSymbol` интерфейсе, соответствующем функции-заглушке ускорителя.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
