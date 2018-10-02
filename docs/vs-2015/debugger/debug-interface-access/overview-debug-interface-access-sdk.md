---
title: Обзор (доступа к интерфейсу отладки пакета SDK) | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8de5b25b1ece8c4523ba222a97f1107d2275ba3a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562331"
---
# <a name="overview-debug-interface-access-sdk"></a>Общие сведения (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Обзор (Отладка интерфейса Access SDK)](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/overview-debug-interface-access-sdk).  
  
Используйте пакет SDK для доступа к данным отладки Microsoft. Пакет SDK для доступа к интерфейсу отладки предоставляет COM набор API, который избавляет от необходимости изменять код каждый раз, когда Майкрософт изменяет формат отладочной информации. Пакет SDK для доступа к интерфейсу отладки также позволяет считывать из набор select отладочной информации в PDB-файл и .dbg файлы, созданные на предыдущих версиях [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] 5.0 и более поздних версиях.  
  
 Каждый интерфейс в пакете SDK для доступа к интерфейсу отладки представляет объект COM, за исключением там, где указано обратное. Дополнительные интерфейсы и тем самым дополнительные объекты, созданные с помощью явных запросов, такие как [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) или [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), а не путем вызова `QueryInterface` на существующие указатели интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)



