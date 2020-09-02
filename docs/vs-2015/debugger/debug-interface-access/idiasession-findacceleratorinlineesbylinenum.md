---
title: 'IDiaSession:: Финдакцелераторинлинисбилиненум | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 386c87aa-f7b2-4d38-9dd6-fffba9ff01f0
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f388671f7efeeefa05704d934ccf5307578e7d3e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150454"
---
# <a name="idiasessionfindacceleratorinlineesbylinenum"></a>IDiaSession::findAcceleratorInlineesByLinenum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает перечисление символов для встраиваемых кадров, соответствующих указанному исходному расположению.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findAcceleratorInlineeLinesByName (   
   IDiaSymbol*           parent,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 colnum,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `parent`  
 окне Объект `IDiaSymbol` , соответствующий функции-заглушке ускорителя, для которой необходимо выполнить поиск.  
  
 `file`  
 окне `IDiaSourceFile` Источник исходного расположения.  
  
 `linenum`  
 окне Номер строки исходного расположения.  
  
 `colnum`  
 окне Номер столбца исходного расположения.  
  
 `ppResult`  
 заполняет Указатель на `IDiaEnumLineNumbers` указатель интерфейса, который инициализируется с помощью результата.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
