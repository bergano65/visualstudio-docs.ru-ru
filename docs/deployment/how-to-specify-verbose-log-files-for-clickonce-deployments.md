---
title: Как выполнить Указание подробных файлов журнала для развертываний ClickOnce | Документация Майкрософт
ms.date: 11/04/2016
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
ms.openlocfilehash: 1c00dd94c9d8ad6702a7f54e461b50f476f0be33
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53840256"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Как выполнить Указание подробных файлов журнала для развертываний ClickOnce
[!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] поддерживает файлы журналов действий для всех развертываний. В этих журналах содержатся подробные сведения, относящиеся к установке, инициализации, обновление и удаление [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] развертывания. Для более подробной информации, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] операции записи в файлы журнала, используйте редактор реестра (*regedit.exe*) для указания уровня детализации.  
  
> [!CAUTION]
>  Неправильное использование редактора реестра может привести к серьезным проблемам, может потребоваться переустановка операционной системы. Используйте редактор реестра на свой страх и риск.  
  
 Следующая процедура описывает способы указания уровня детализации для [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] файлы журнала для текущего пользователя. Чтобы снизить уровень детализации, удалите это значение реестра.  
  
### <a name="to-specify-verbose-log-files"></a>Чтобы указать файлы подробного журнала  
  
1.  Откройте *Regedit.exe*.  
  
2.  Перейдите к узлу **HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment**.  
  
3.  При необходимости создайте новый строковый параметр с именем `LogVerbosityLevel`.  
  
4.  Установите для `LogVerbosityLevel` значение `1`.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертываний ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)