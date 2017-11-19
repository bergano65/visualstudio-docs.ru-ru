---
title: "Как: просмотр документов скриптов | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords: Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: "22"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: af4230a0d0bec680be1231f37e4e0bfbe51bc459
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-view-script-documents"></a>Практическое руководство. Просмотр документов скриптов
В более ранних версиях [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] клиентские файлы скриптов, созданные из серверных скриптов, появлялись в окне обозревателя скриптов. Окно обозревателя скриптов часто было скрыто, так что доступность клиентского скрипта была не всегда очевидна.  
  
 В [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] файлы клиентских скриптов, созданные из серверных скриптов, отображаются в обозревателе решений, который по умолчанию отображается. Окно обозревателя скриптов больше не используется.  
  
 Клиентские файлы скриптов отображаются только в режиме отладки или режиме приостановки. Они отображаются в **документов скрипта** узла.  
  
 Серверные файлы скриптов отображаются всегда. Они отображаются в  **\<Pathname веб-сайта >** узла. Имя узла напоминает в этом примере:`c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Просмотр документа серверного скрипта  
  
1.  В **обозревателе решений**откройте  **\<Pathname веб-сайта >** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Серверная часть скрипта откроется в окне исходного кода.  
  
### <a name="to-view-a-client-side-script-document"></a>Просмотр документа клиентского скрипта  
  
1.  В **обозревателе решений**откройте **документов скрипта** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Клиентская часть скрипта откроется в окне исходного кода.  
  
## <a name="see-also"></a>См. также  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)