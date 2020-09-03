---
title: Создание типов проектов | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, new
- projects [Visual Studio SDK], new project types
ms.assetid: bdb2d22e-d622-450c-bb2d-98152a745fcf
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bbe65d1615603e4dc7546dbfe3530093c62528e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155028"
---
# <a name="creating-project-types"></a>Создание типов проектов
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Можно расширить [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , создав новый тип проекта. Чтобы создать новый тип проекта, необходимо ознакомиться с некоторыми концепциями и выполнить ряд действий. В следующих разделах приводятся общие сведения о создании типов проектов.  
  
## <a name="in-this-section"></a>в этом разделе  
 [Проектные решения для типа проекта](../../extensibility/internals/project-type-design-decisions.md)  
 Обсуждаются элементы, сохраняемость файлов проекта и обязательства по проектированию механику, которые необходимо выполнить перед созданием нового типа проекта.  
  
 [Контрольный список. Создание новых типов проектов](../../extensibility/internals/checklist-creating-new-project-types.md)  
 Содержит общие сведения о шагах, которые необходимо выполнить для создания нового типа проекта, который поддерживает задачи программирования в виде редактирования кода и компиляции, сборки, отладки и развертывания приложений в проекте.  
  
 [Создание экземпляров проекта с помощью фабрик проектов](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)  
 Содержит сведения о том, как предоставить и использовать фабрику проектов для создания экземпляров нового проекта.  
  
 [Регистрация типа проекта](../../extensibility/internals/registering-a-project-type.md)  
 Предоставляет образцы кода инструкций из реестра, которые предоставляют пути и данные по умолчанию, а также таблицу, содержащую записи из скрипта реестра для каждой инструкции.  
  
 [Сохранение проекта](../../extensibility/internals/project-persistence.md)  
 Обсуждается использование `IPersistFileFormat` для сохранения как файловых, так и нефайловых объектов проекта.  
  
 [Использование MSBuild](../../extensibility/internals/using-msbuild.md)  
 Описывает, как тип проекта может использовать [!INCLUDE[vstecmsbuild](../../includes/vstecmsbuild-md.md)] механизм сборки, чтобы разрешить пользователям выполнять сборку из [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] и из командной строки.  
  
## <a name="related-sections"></a>См. также  
 [Вспомогательные средства просмотра символов](../../extensibility/internals/supporting-symbol-browsing-tools.md)  
 Описание архитектуры средств просмотра кода, таких как **Обозреватель объектов** и окно **представление классов** . Описывает интерфейсы и методы, используемые для реализации обзора объектов в VSPackage.  
  
 [Добавление проекта и шаблонов элементов проекта](../../extensibility/internals/adding-project-and-project-item-templates.md)  
 Описывает важность, которую играют проекты при определении того, какой редактор используется при открытии элемента проекта и о том, как можно манипулировать ресурсами проекта.  
  
 [Установка пакетов VSPackage с помощью установщика Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md)  
 Здесь показано, как предоставить пакету VSPackage собственное уникальное удостоверение и как заключить в пакеты библиотеки DLL VSPackage и другие сведения в установщик Windowsном пакете (. MSI-файл) для развертывания на клиентах.  
  
 [Иерархии в Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)  
 Описывает [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] , как представления и иерархии адресов.  
  
 [VSPackages](../../extensibility/internals/vspackages.md)  
 Содержит общие сведения о VSPackage, устанавливаемый COM-объект, который расширяет [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] среду и обсуждает реализацию собственного пакета VSPackage.  
  
 [Типы проектов](../../extensibility/internals/project-types.md)  
 Описывает, как использовать проекты для изменения кода, компиляции и построения кода, а также выполнения и отладки кода и предоставляет ссылки на подробные разделы, посвященные созданию типов проектов.
