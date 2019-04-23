---
title: Практическое руководство. Устранение неполадок в службах | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- services, troubleshooting
ms.assetid: 001551da-4847-4f59-a0b2-fcd327d7f5ca
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5311aa3ff390611942aa91cb1f2a53ca5a76258d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60074312"
---
# <a name="how-to-troubleshoot-services"></a>Практическое руководство. Устранение неполадок, связанных со службами
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Существует несколько распространенных проблем, которые могут возникнуть при попытке получения службы.  
  
- Служба не зарегистрирована с [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
- Служба запрашивается, тип интерфейса, а не тип службы.  
  
- Пакет VSPackage, запрашивающего службу не был размещен.  
  
- Поставщик неверной службе используется.  
  
  Если запрошенная служба недоступна, вызов <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> возвращает значение null. Вы должны всегда тестировать со значением NULL после выполнения запроса службы:  
  
```csharp  
IVsActivityLog log =   
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
if (log == null) return;  
```  
  
### <a name="to-troubleshoot-a-service"></a>Устранение неполадок со службой  
  
1. Проверьте в системный реестр, чтобы увидеть ли службы был правильно зарегистрирован. Дополнительные сведения см. в разделе [регистрация служб](../misc/registering-services.md).  
  
     В следующем фрагменте файла .reg показано, как служба SVsTextManager может быть зарегистрирована:  
  
    ```  
    [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
    @="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
    "Name"="SVsTextManager"  
    ```  
  
     В приведенном выше примере номер версии — версия [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как 12.0 и 14.0, ключ {F5E7E71D-1401-11d1-883B-0000F87579D2} является идентификатором службы (SID) службы, SVsTextManager и {значение по умолчанию F5E7E720-1401-11D1-883B-0000F87579D2} является GUID диспетчера текстов VSPackage, который предоставляет службу пакета.  
  
2. Используйте тип службы, а не тип интерфейса, при вызове GetService. При запросе к службе из [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], <xref:Microsoft.VisualStudio.Shell.Package> извлекает идентификатор GUID из типа. Не удалось найти службу, если выполняются следующие условия:  
  
    1. Тип интерфейса передается GetService вместо типа службы.  
  
    2. Идентификатор GUID не явно назначенный интерфейсу. Таким образом система создает значение по умолчанию идентификатор GUID для объекта при необходимости.  
  
3. Убедитесь, что VSPackage, запрашивающего службу размещения. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] узлы VSPackage, после его создания и перед вызовом метода <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A>.  
  
     Если у вас есть код в конструктор VSPackage, который нуждается в обслуживании, переместите его в метод Initialize.  
  
4. Убедитесь, что вы используете правильный доступ к службе.  
  
     Не все поставщики услуг похожи. Поставщик услуг, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] передает в окно инструментов отличается от того, он передает VSPackage. Поставщик услуг окно инструмента знает о <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>, но он не знает о <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Вы можете вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> получить поставщик службы из VSPackage в окне инструментов.  
  
     Если окно инструментов содержит пользовательский элемент управления или любой другой контейнер элемента управления, контейнер будет размещаться по модели компонентов Windows и не будет доступа к любому [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] служб. Вы можете вызвать <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> получить поставщик служб VSPackage из контейнера элемента управления.  
  
## <a name="see-also"></a>См. также  
 [Список доступных служб](../extensibility/internals/list-of-available-services.md)   
 [Использование и предоставление служб](../extensibility/using-and-providing-services.md)   
 [Основные компоненты службы](../extensibility/internals/service-essentials.md)
