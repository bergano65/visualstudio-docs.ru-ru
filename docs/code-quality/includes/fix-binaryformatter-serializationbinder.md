---
ms.openlocfilehash: 557d811e2eeaf926cb958471d214fc23c50a25f2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "87471585"
---
- Используйте вместо этого безопасный сериализатор и **не позволяйте злоумышленнику указывать произвольный тип для десериализации**. Дополнительные сведения см. в разделе [предпочтительные альтернативы](/dotnet/standard/serialization/binaryformatter-security-guide#preferred-alternatives).
- Сделайте сериализованные данные несанкционированными. После сериализации криптографически подписывает сериализованные данные. Перед десериализациюм проверьте криптографическую подпись. Защитите криптографический ключ от раскрывать и разрабатывать для смены ключей.
- Этот параметр делает код уязвимым к атакам типа "отказ в обслуживании" и возможным атакам удаленного выполнения кода в будущем. Дополнительные сведения см. в разделе [BinaryFormatter Security Guide](/dotnet/standard/serialization/binaryformatter-security-guide). Ограничьте десериализованные типы. Реализуйте пользовательский интерфейс <xref:System.Runtime.Serialization.SerializationBinder?displayProperty=nameWithType> . Перед десериализацией задайте `Binder` для свойства экземпляр пользовательского класса <xref:System.Runtime.Serialization.SerializationBinder> во всех путях кода. В переопределенном <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> методе, если тип является непредвиденным, вызовите исключение для отмены десериализации.
