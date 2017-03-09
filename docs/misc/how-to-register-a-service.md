---
title: "Практическое руководство. Регистрация службы | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "службы, регистрация"
ms.assetid: d086be78-ec3c-43cc-b799-5180a71e19f1
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# Практическое руководство. Регистрация службы
Платформа Managed Package Framework \(MPF\) предоставляет атрибуты для управления регистрацией управляемых служб. Служебная программа RegPkg использует эти атрибуты для регистрации службы в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Пример  
 Приведенный ниже код взят из [Примеры VSSDK](../misc/vssdk-samples.md).  
  
 [!code-vb[VSSDKRegisterService#1](../misc/codesnippet/VisualBasic/how-to-register-a-service_1.vb)]
 [!code-cs[VSSDKRegisterService#1](../misc/codesnippet/CSharp/how-to-register-a-service_1.cs)]  
  
 <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute> регистрирует службу SMyGlobalService в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Дополнительные сведения о сопоставлениях <xref:Microsoft.VisualStudio.Shell.DefaultRegistryRootAttribute> и <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> см. в разделе [Регистрация и Отмена регистрации VSPackages.](../extensibility/registering-and-unregistering-vspackages.md).  
  
 Чтобы зарегистрировать службу, которая заменяет другую службу с тем же именем, используйте <xref:Microsoft.VisualStudio.Shell.ProvideServiceOverrideAttribute> вместо <xref:Microsoft.VisualStudio.Shell.ProvideServiceAttribute>.  
  
## Отказоустойчивость  
 Чтобы упростить повторную компиляцию поставщика службы без изменения клиента службы или наоборот, можно определить службу и ее интерфейсы в отдельном модуле сборки. Приведенный ниже код взят из файла IMyGlobalService.cs примера Reference.Services \(C\#\).  
  
 [!code-vb[VSSDKRegisterService#2](../misc/codesnippet/VisualBasic/how-to-register-a-service_2.vb)]
 [!code-cs[VSSDKRegisterService#2](../misc/codesnippet/CSharp/how-to-register-a-service_2.cs)]  
  
 Атрибут <xref:System.Runtime.InteropServices.ComVisibleAttribute> необходим для получения интерфейса из неуправляемого кода.  
  
> [!NOTE]
>  Хотя можно использовать один и тот же тип или идентификатор GUID как для службы, так и для интерфейса, мы рекомендуем разделять их, так как служба может предоставлять различные интерфейсы.  
  
## См. также  
 [Registering VSPackages](http://msdn.microsoft.com/ru-ru/31e6050f-1457-4849-944a-a3c36b76f3dd)   
 [Основы службы](../extensibility/internals/service-essentials.md)