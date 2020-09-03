---
title: Общие сведения (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- user-defined types
- .dbg files
- modules
- interfaces [DIA SDK]
- DBG files
- procedures [DIA SDK]
- executable files
- COM objects, in DIA SDK
- compilands
- executable images
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7374b03da42e34e8ac3be8c7cc570769d9cfd1ff
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68179200"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Используйте пакет SDK DIA для доступа к информации об отладке Майкрософт. Пакет SDK для DIA предоставляет набор API на основе COM, который устраняет необходимость в перезаписи кода всякий раз, когда Майкрософт изменяет формат отладочной информации. DIA SDK также позволяет считывать данные из выбранного набора предыдущих версий отладочной информации, расположенной в файлах PDB и DBG, созданных в [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] версиях 5,0 и более поздних.  
  
 Каждый интерфейс в пакете SDK для DIA представляет отдельный COM-объект, за исключением случаев, где указано иное. Дополнительные интерфейсы и, таким образом, дополнительные объекты создаются с помощью явных запросов, таких как [идиадатасаурце:: опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession:: финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` в существующих указателях интерфейса.  
  
## <a name="see-also"></a>См. также:  
 [Идиадатасаурце:: Опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)
