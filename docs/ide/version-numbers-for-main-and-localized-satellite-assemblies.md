---
title: Номера версий основных и вспомогательных локализованных сборок | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- satellite assemblies, version numbers
- SatelliteContractVersionAttribute
- version numbers, assemblies
- assemblies [Visual Studio], version numbers
- versioning, assemblies
ms.assetid: 5489aea1-57b4-4561-9bb4-24d490269602
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 361a2ff0d35c71250acca59788c199fbe69f57ff
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="version-numbers-for-main-and-localized-satellite-assemblies"></a>Номера версий основных и вспомогательных локализованных сборок
Класс <xref:System.Resources.SatelliteContractVersionAttribute> обеспечивает поддержку управления версиями для основной сборки, которая использует локализованные ресурсы с помощью диспетчера ресурсов. Применение <xref:System.Resources.SatelliteContractVersionAttribute> к основной сборке приложения позволяет обновить и повторно развернуть ее, не обновляя вспомогательные сборки. Например, можно использовать класс <xref:System.Resources.SatelliteContractVersionAttribute> с пакетом обновления, который предоставляет новые ресурсы только после перестройки и повторного развертывания вспомогательных сборок. Чтобы ваши локализованные ресурсы были доступны, версия контракта для вспомогательной сборки в основной сборке должна соответствовать классу <xref:System.Reflection.AssemblyVersionAttribute> вспомогательных сборок. Необходимо указать точный номер версии в <xref:System.Resources.SatelliteContractVersionAttribute>; подстановочные знаки, такие как "*", не допускаются. Дополнительные сведения см. в разделе [Извлечение ресурсов](/dotnet/framework/resources/retrieving-resources-in-desktop-apps).  
  
## <a name="updating-assemblies"></a>Обновление сборок  
 Класс <xref:System.Resources.SatelliteContractVersionAttribute> позволяет обновить основную сборку, не затрагивая вспомогательную, и наоборот. При обновлении основной сборки ее номер версии изменяется. Если вы хотите и дальше использовать имеющиеся вспомогательные сборки, измените номер версии основной сборки, а номер версии контракта для вспомогательной сборки оставьте без изменений. Например, в первом выпуске основная сборка может иметь версию 1.0.0.0. Версия контракта для вспомогательной сборки и версия самой вспомогательной сборки также будут иметь номер 1.0.0.0. Если вам нужно обновить основную сборку для пакета обновления, можно изменить ее версию на 1.0.0.1, оставив у контракта для вспомогательной сборки и самой вспомогательной сборки версию 1.0.0.0.  
  
 Если требуется обновить вспомогательную сборку без основной сборки, измените <xref:System.Reflection.AssemblyVersionAttribute> вспомогательной сборки. Вместе со вспомогательной сборкой вам нужно отправить сборку политики, которая указывает, что новая вспомогательная сборка совместима со старой. Дополнительные сведения о политиках см. в разделе [Обнаружение сборок в среде выполнения](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).  
  
 В следующем примере кода показано, как задать версию контракта для вспомогательной сборки. Код можно поместить в скрипт сборки либо в файл AssemblyInfo.vb или AssemblyInfo.cs.  
  
```vb  
<Assembly: SatelliteContractVersionAttribute("4.3.2.1")>  
  
```  
  
```csharp  
[assembly: SatelliteContractVersionAttribute("4.3.2.1")]  
```  
  
## <a name="see-also"></a>См. также  
 [Обнаружение сборок в среде выполнения](/dotnet/framework/deployment/how-the-runtime-locates-assemblies)   
 [Настройка атрибутов сборки](/dotnet/framework/app-domains/set-assembly-attributes)   
 [Безопасность и локализованные вспомогательные сборки](../ide/security-and-localized-satellite-assemblies.md)   
 [Локализация приложений](../ide/localizing-applications.md)   
 [Глобализация и локализация приложений](../ide/globalizing-and-localizing-applications.md)