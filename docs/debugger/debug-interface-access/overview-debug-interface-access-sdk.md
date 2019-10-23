---
title: Общие сведения (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1e4269c620247f256d2cfae2e84b76ff60fcf9ba
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738603"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
Используйте пакет SDK DIA для доступа к информации об отладке Майкрософт. Пакет SDK для DIA предоставляет набор API на основе COM, который устраняет необходимость в перезаписи кода всякий раз, когда Майкрософт изменяет формат отладочной информации. DIA SDK также позволяет считывать данные из выбранного набора предыдущих версий отладочной информации, расположенной в файлах PDB и DBG, созданных [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] версиями 5,0 и более поздних версий.

 Каждый интерфейс в пакете SDK для DIA представляет отдельный COM-объект, за исключением случаев, где указано иное. Дополнительные интерфейсы и, таким образом, дополнительные объекты создаются с помощью явных запросов, таких как [идиадатасаурце:: опенсессион](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession:: финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` для существующих указателей интерфейса.

## <a name="see-also"></a>См. также
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)