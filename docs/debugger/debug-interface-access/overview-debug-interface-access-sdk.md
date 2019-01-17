---
title: Обзор (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b747d888ecea4235e34acd169b9230884c7454ef
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53843967"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
Используйте пакет SDK для доступа к данным отладки Microsoft. Пакет SDK для доступа к интерфейсу отладки предоставляет COM набор API, который избавляет от необходимости изменять код каждый раз, когда Майкрософт изменяет формат отладочной информации. Пакет SDK для доступа к интерфейсу отладки также позволяет считывать из набор select отладочной информации в PDB-файл и .dbg файлы, созданные на предыдущих версиях [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 5.0 и более поздних версиях.  
  
 Каждый интерфейс в пакете SDK для доступа к интерфейсу отладки представляет объект COM, за исключением там, где указано обратное. Дополнительные интерфейсы и тем самым дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующие указатели интерфейса.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)