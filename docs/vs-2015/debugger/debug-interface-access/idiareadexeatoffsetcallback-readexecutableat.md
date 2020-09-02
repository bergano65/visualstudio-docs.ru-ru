---
title: 'Идиареадексеатоффсеткаллбакк:: Реадексекутаблеат | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtOffsetCallback::ReadExecutableAt method
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1ac5452437ab6fdec3eb68baf46aeeab8434df4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538867"
---
# <a name="idiareadexeatoffsetcallbackreadexecutableat"></a>IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает указанное число байтов, начиная с указанного смещения, из исполняемого файла.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 филеоффсет  
 окне Смещение в исполняемом файле, с которого начинается чтение.  
  
 cbData  
 окне Число байтов для чтения.  
  
 пкбдата  
 заполняет Возвращает число считанных байтов.  
  
 data[]  
 [вход, выход] Массив, который заполняется байтами, считанными из файла.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается кодом поддержки DIA для загрузки байтов данных из исполняемого файла с использованием абсолютного смещения. Этот метод вызывается для поддержки метода [идиадатасаурце:: лоаддатафорексе](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## <a name="see-also"></a>См. также:  
 [идиареадексеатоффсеткаллбакк](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)
