---
title: 'Идиареадексеатрвакаллбакк:: Реадексекутаблеатрва | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187271"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает указанное число байтов, начиная с указанного относительного виртуального адреса (RVA) из исполняемого файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `relativeVirtualAddress`  
 окне RVA в исполняемом файле, с которого начинается чтение.  
  
 `cbData`  
 окне Число байтов для чтения.  
  
 `pcbData`  
 заполняет Возвращает число считанных байтов.  
  
 `data[]`  
 [вход, выход] Массив, который заполняется байтами, считанными из файла.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается кодом поддержки DIA для загрузки байт данных из исполняемого файла с использованием относительного виртуального адреса. Этот метод вызывается для поддержки метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиареадексеатрвакаллбакк](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
