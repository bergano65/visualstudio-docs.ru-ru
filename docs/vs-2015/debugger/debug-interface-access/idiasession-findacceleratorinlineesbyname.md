---
title: IDiaSession::findAcceleratorInlineesByName | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: e203e5c2-6563-43fa-be56-3063955043ab
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 47883395ec12cac60d3a21651432f5ac21cc64a4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151752"
---
# <a name="idiasessionfindacceleratorinlineesbyname"></a>IDiaSession::findAcceleratorInlineesByName
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает перечисление символов для встроенных кадров, соответствующих указанному имени встроенной функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSymbols**     ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `name`  
 окне Имя встроенной функции для поиска.  
  
 `option`  
 окне Параметры поиска имен, используемые при поиске встраиваемых кадров, соответствующих `name` . Дополнительные сведения см. в разделе [перечисление намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md).  
  
 `ppResult`  
 заполняет Указатель на `IDiaEnumSymbols` указатель интерфейса, который инициализируется с помощью результата.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Эта функция выполняет поиск встроенных функций только в функциях-заглушках ускорителя. Он игнорирует записи собственных процедур C++.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
