---
title: Практическое руководство. Указание подробных файлов журнала для развертываний ClickOnce | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 78fa278952004348e035a675a1e159b2164285b1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441605"
---
# <a name="how-to-specify-verbose-log-files-for-clickonce-deployments"></a>Практическое руководство. Указание подробных файлов журнала для развертывания ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] поддерживает файлы журналов действий для всех развертываний. В этих журналах содержатся подробные сведения, относящиеся к установке, инициализации, обновление и удаление [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] развертывания. Для более подробной информации, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] операции записи в файлы журнала, используйте редактор реестра (**regedit.exe**) для указания уровня детализации.  
  
> [!CAUTION]
> Неправильное использование редактора реестра может привести к серьезным проблемам, может потребоваться переустановка операционной системы. Используйте редактор реестра на свой страх и риск.  
  
 Следующая процедура описывает способы указания уровня детализации для [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] файлы журнала для текущего пользователя. Чтобы снизить уровень детализации, удалите это значение реестра.  
  
### <a name="to-specify-verbose-log-files"></a>Чтобы указать файлы подробного журнала  
  
1. Откройте **Regedit.exe**.  
  
2. Перейдите к узлу `HKEY_CURRENT_USER\Software\Classes\Software\Microsoft\Windows\CurrentVersion\Deployment`.  
  
3. При необходимости создайте новый строковый параметр с именем `LogVerbosityLevel`.  
  
4. Установите для `LogVerbosityLevel` значение `1`.  
  
## <a name="see-also"></a>См. также  
 [Устранение неполадок развертывания ClickOnce](../deployment/troubleshooting-clickonce-deployments.md)
