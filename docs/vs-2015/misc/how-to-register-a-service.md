---
title: 'Практическое: регистрация службы | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- services, registering
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
manager: douge
ms.openlocfilehash: a242a13893c7cd303adfe266c9609b7a71d251ba
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561930"
---
# <a name="how-to-register-a-service"></a>Практическое руководство. Регистрация службы
Платформа Managed Package Framework (MPF) предоставляет атрибуты для управления регистрацией управляемых служб. Служебная программа RegPkg использует эти атрибуты для регистрации службы в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="example"></a>Пример  
 Приведенный ниже код взят из [примеры VSSDK](../misc/vssdk-samples.md).  
  
 [!code-csharp[VSSDKRegisterService#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#1)]
 [!code-vb[VSSDKRegisterService#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#1)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> Регистрирует службу SMyGlobalService [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Дополнительные сведения о <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> и <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, см. в разделе [регистрация и Отмена регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Чтобы зарегистрировать службу, которая заменяет другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> вместо <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## <a name="robust-programming"></a>Отказоустойчивость  
 Чтобы упростить повторную компиляцию поставщика службы без изменения клиента службы или наоборот, можно определить службу и ее интерфейсы в отдельном модуле сборки. Приведенный ниже код взят из файла IMyGlobalService.cs примера Reference.Services (C#).  
  
 [!code-csharp[VSSDKRegisterService#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkregisterservice/cs/vssdkregisterservicepackage.cs#2)]
 [!code-vb[VSSDKRegisterService#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkregisterservice/vb/vssdkregisterservicepackage.vb#2)]  
  
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> Необходим для получения интерфейса из неуправляемого кода.  
  
> [!NOTE]
>  Хотя можно использовать один и тот же тип или идентификатор GUID как для службы, так и для интерфейса, мы рекомендуем разделять их, так как служба может предоставлять различные интерфейсы.  
  
## <a name="see-also"></a>См. также  
 [Регистрация пакетов VSPackage](http://msdn.microsoft.com/en-us/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)