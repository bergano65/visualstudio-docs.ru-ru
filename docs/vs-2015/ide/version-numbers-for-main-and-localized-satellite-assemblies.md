---
title: Номера версий основных и вспомогательных локализованных сборок | Документы Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a5c6d5e16a77a8c04964beb38e21ebf82ede7f0b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49223045"
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Номера версий основных и вспомогательных локализованных сборок
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Класс <xref:System.Resources.SatelliteContractVersionAttribute> обеспечивает поддержку управления версиями для основной сборки, которая использует локализованные ресурсы с помощью диспетчера ресурсов. Применение <xref:System.Resources.SatelliteContractVersionAttribute> к основной сборке приложения позволяет обновить и повторно развернуть ее, не обновляя вспомогательные сборки. Например, можно использовать класс <xref:System.Resources.SatelliteContractVersionAttribute> с пакетом обновления, который предоставляет новые ресурсы только после перестройки и повторного развертывания вспомогательных сборок. Чтобы ваши локализованные ресурсы были доступны, версия контракта для вспомогательной сборки в основной сборке должна соответствовать классу <xref:System.Reflection.AssemblyVersionAttribute> вспомогательных сборок. Необходимо указать точный номер версии в <xref:System.Resources.SatelliteContractVersionAttribute>; подстановочные знаки, такие как "*", не допускаются. Дополнительные сведения см. в разделе [Извлечение ресурсов](http://msdn.microsoft.com/library/eca16922-1c46-4f68-aefe-e7a12283641f).  
  
## <a name="updating-assemblies"></a>Обновление сборок  
 Класс <xref:System.Resources.SatelliteContractVersionAttribute> позволяет обновить основную сборку, не затрагивая вспомогательную, и наоборот. При обновлении основной сборки ее номер версии изменяется. Если вы хотите и дальше использовать имеющиеся вспомогательные сборки, измените номер версии основной сборки, а номер версии контракта для вспомогательной сборки оставьте без изменений. Например, в первом выпуске основная сборка может иметь версию 1.0.0.0. Версия контракта для вспомогательной сборки и версия самой вспомогательной сборки также будут иметь номер 1.0.0.0. Если вам нужно обновить основную сборку для пакета обновления, можно изменить ее версию на 1.0.0.1, оставив у контракта для вспомогательной сборки и самой вспомогательной сборки версию 1.0.0.0.  
  
 Если требуется обновить вспомогательную сборку без основной сборки, измените <xref:System.Reflection.AssemblyVersionAttribute> вспомогательной сборки. Вместе со вспомогательной сборкой вам нужно отправить сборку политики, которая указывает, что новая вспомогательная сборка совместима со старой. Дополнительные сведения о политиках см. в разделе [Обнаружение сборок в среде выполнения](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).  
  
 В следующем примере кода показано, как задать версию контракта для вспомогательной сборки. Код можно поместить в скрипт сборки либо в файл AssemblyInfo.vb или AssemblyInfo.cs.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>См. также  
 [Обнаружение сборок в среде выполнения](http://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34)   
 [Настройка атрибутов сборки](http://msdn.microsoft.com/library/36a98a81-b5b5-4c19-912a-11f91eff7f4e)   
 [Безопасность и локализованные вспомогательные сборки](../ide/security-and-localized-satellite-assemblies.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)

