---
title: 'Как: Указание подробных файлов журнала для развертывания ClickOnce | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- logs, ClickOnce deployment
- ClickOnce deployment, logging
ms.assetid: 0807a28d-2e40-4a51-ab10-308d808ded6b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8153625ec875cb54b0fc7b626d0cef61df2e9b71
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31557987"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Практическое руководство. Указание подробных файлов журнала для развертывания ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] поддерживает файлы журналов действий для всех развертываний. В этих журналах содержатся подробные сведения, относящиеся к установке, инициализации, обновление и удаление [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания. Для более подробной информации, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] записи в файлы журнала, используйте редактор реестра (**regedit.exe**) для указания уровня детализации.  
  
> [!CAUTION]
>  Неправильное использование редактора реестра может привести к серьезным проблемам, которые могут потребовать переустановки операционной системы. Используйте редактор реестра на свой страх и риск.  
  
 Следующая процедура описывает, как для указания уровня детализации для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлы журнала для текущего пользователя. Чтобы снизить уровень детализации, удалите это значение реестра.  
  
### <a name="to-specify-verbose-log-files"></a>Указание подробных файлов журнала  
  
1.  Откройте **Regedit.exe**.  
  
2.  Перейдите к узлу `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3.  При необходимости создайте новый строковый параметр с именем `LogVerbosityLevel`.  
  
4.  Задать `LogVerbosityLevel` значение `1`.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)