---
title: Практическое руководство. Регистрация службы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: jillfra
ms.openlocfilehash: 0ec69fa123775cb477195d4022fb439fb990f415
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "59002819"
---
# <a name="how-to-register-a-service"></a>Практическое руководство. Регистрация службы
Платформа Managed Package Framework (MPF) предоставляет атрибуты для управления регистрацией управляемых служб. Служебная программа RegPkg использует эти атрибуты для регистрации службы в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Пример  
 Приведенный ниже код взят из [примеры VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> регистрирует службу SMyGlobalService в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения о <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> и <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Чтобы зарегистрировать службу, которая заменяет другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> вместо <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Чтобы упростить повторную компиляцию поставщика службы без изменения клиента службы или наоборот, можно определить службу и ее интерфейсы в отдельном модуле сборки. Приведенный ниже код взят из файла IMyGlobalService.cs примера Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 Атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> необходим для получения интерфейса из неуправляемого кода.  
  
> [!NOTE]
>  Хотя можно использовать один и тот же тип или идентификатор GUID как для службы, так и для интерфейса, мы рекомендуем разделять их, так как служба может предоставлять различные интерфейсы.  
  
## <a name="see-also"></a>См. также  
 [Регистрация пакетов VSPackage](../extensibility/internals/registering-vspackages.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)