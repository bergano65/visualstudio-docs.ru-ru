---
title: "Как: Устранение неполадок службы | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 71ac3cda8e3df935ab743fed7aa94a5152c152a5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-troubleshoot-services"></a>Как: диагностика служб
Существует несколько распространенных проблем, которые могут возникнуть при попытке получения службы.  
  
-   Служба не зарегистрирована в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
-   Служба запрошена, тип интерфейса, а не тип службы.  
  
-   Пакет VSPackage, запрашивающего службу не был размещен.  
  
-   Используется неправильный доступ к службе.  
  
 Если запрошенная служба недоступна, вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> возвращает значение null. Следует всегда проверять значения NULL после выполнения запроса службы:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Устранение неполадок со службой  
  
1.  Проверьте системный реестр, чтобы увидеть службы правильно зарегистрирован ли. Дополнительные сведения см. в разделе [как: обслуживать](../extensibility/how-to-provide-a-service.md).  
  
     В следующем фрагменте файла .reg показано, как служба SVsTextManager может быть зарегистрировано.  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     В приведенном выше примере номер версии — версия [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], такие как 12.0 и 14.0, ключ {F5E7E71D-1401-11d1-883B-0000F87579D2} является идентификатором службы (SID) службы, SVsTextManager и {значение по умолчанию F5E7E720-1401-11D1-883B-0000F87579D2} является GUID диспетчера текстов VSPackage, который предоставляет службу пакета.  
  
2.  Используйте тип службы, а не типа интерфейса, если вызывать GetService. При запросе к службе из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], <xref:Microsoft.VisualStudio.Shell.Package> извлекает идентификатор GUID из типа. Не удалось найти службу, если выполняются следующие условия:  
  
    1.  Тип интерфейса передается GetService вместо типа службы.  
  
    2.  Идентификатор GUID не назначается явно интерфейс. Таким образом система создает GUID по умолчанию для объекта при необходимости.  
  
3.  Убедитесь, что VSPackage, запрашивающего службу размещения. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]сайты VSPackage, после его создания и перед вызовом метода <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Если у вас есть код в конструктор VSPackage, который нуждается в обслуживании, переместите его метода инициализации.  
  
4.  Убедитесь, что вы используете правильный доступ к службе.  
  
     Не все поставщики услуг похожи. Поставщик услуг, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] передает в окно инструментов отличается от передачей пакетов VSPackage. Поставщик услуг окна инструментов знает о <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, но не знает о <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Можно вызвать метод <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения от поставщика услуг VSPackage в окне инструментов.  
  
     Если окно инструментов содержит пользовательский элемент управления или любой другой контейнер элемента управления, контейнер будет размещен в модели компонента Windows и не будет доступа к любому [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] служб. Можно вызвать метод <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> для получения поставщика услуг VSPackage из контейнера элемента управления.  
  
## <a name="see-also"></a>См. также  
 [Список доступных служб](../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставления услуг](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)