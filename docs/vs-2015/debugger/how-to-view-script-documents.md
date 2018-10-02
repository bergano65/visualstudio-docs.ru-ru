---
title: 'Практическое: просмотр документов скриптов | Документация Майкрософт'
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
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dc24c5e9c2332516cbf939e14581a2df7bea44eb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569392"
---
# <a name="how-to-view-script-documents"></a>Практическое руководство. Просмотр документов скриптов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: View Script Documents](https://docs.microsoft.com/visualstudio/debugger/how-to-view-script-documents).  
  
В более ранних версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] клиентские файлы скриптов, созданные из серверных скриптов, появлялись в окне обозревателя скриптов. Окно обозревателя скриптов часто было скрыто, так что доступность клиентского скрипта была не всегда очевидна.  
  
 В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] файлы клиентских скриптов, созданные из серверных скриптов, отображаются в обозревателе решений, который по умолчанию отображается. Окно обозревателя скриптов больше не используется.  
  
 Клиентские файлы скриптов отображаются только в режиме отладки или режиме приостановки. Они отображаются в **документы скриптов** узла.  
  
 Серверные файлы скриптов отображаются всегда. Они отображаются в  **\<путь веб-сайта >** узла. Имя узла выглядит следующим образом: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Просмотр документа серверного скрипта  
  
1.  В **обозревателе решений**откройте  **\<путь веб-сайта >** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Серверная часть скрипта откроется в окне исходного кода.  
  
### <a name="to-view-a-client-side-script-document"></a>Просмотр документа клиентского скрипта  
  
1.  В **обозревателе решений**откройте **документы скриптов** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Клиентская часть скрипта откроется в окне исходного кода.  
  
## <a name="see-also"></a>См. также  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)



