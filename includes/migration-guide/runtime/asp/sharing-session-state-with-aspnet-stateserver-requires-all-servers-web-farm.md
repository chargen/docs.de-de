### <a name="sharing-session-state-with-aspnet-stateserver-requires-all-servers-in-the-web-farm-to-use-the-same-net-framework-version"></a><span data-ttu-id="4cc71-101">Für das Freigeben des Sitzungszustands mit Asp.Net StateServer müssen alle Server in der Webfarm dieselbe .NET Framework-Version verwenden</span><span class="sxs-lookup"><span data-stu-id="4cc71-101">Sharing session state with Asp.Net StateServer requires all servers in the web farm to use the same .NET Framework version</span></span>

|   |   |
|---|---|
|<span data-ttu-id="4cc71-102">Details</span><span class="sxs-lookup"><span data-stu-id="4cc71-102">Details</span></span>|<span data-ttu-id="4cc71-103">Wenn ein <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name>-Sitzungszustand aktiviert wird, müssen alle Server in der jeweiligen Webfarm dieselbe Version von .NET Framework verwenden, damit der Zustand ohne Probleme freigegeben werden kann.</span><span class="sxs-lookup"><span data-stu-id="4cc71-103">When enabling <xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=name> session state, all of the servers in the given web farm must use the same version of the .NET Framework in order for state to be properly shared.</span></span>|
|<span data-ttu-id="4cc71-104">Vorschlag</span><span class="sxs-lookup"><span data-stu-id="4cc71-104">Suggestion</span></span>|<span data-ttu-id="4cc71-105">Führen Sie für alle .NET Framework-Versionen auf Webservern, für die ein Zustand freigegeben wird, gleichzeitig ein Upgrade aus.</span><span class="sxs-lookup"><span data-stu-id="4cc71-105">Be sure to upgrade .NET Framework versions on web servers that share state at the same time.</span></span>|
|<span data-ttu-id="4cc71-106">Bereich</span><span class="sxs-lookup"><span data-stu-id="4cc71-106">Scope</span></span>|<span data-ttu-id="4cc71-107">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="4cc71-107">Edge</span></span>|
|<span data-ttu-id="4cc71-108">Version</span><span class="sxs-lookup"><span data-stu-id="4cc71-108">Version</span></span>|<span data-ttu-id="4cc71-109">4.5</span><span class="sxs-lookup"><span data-stu-id="4cc71-109">4.5</span></span>|
|<span data-ttu-id="4cc71-110">Typ</span><span class="sxs-lookup"><span data-stu-id="4cc71-110">Type</span></span>|<span data-ttu-id="4cc71-111">Laufzeit</span><span class="sxs-lookup"><span data-stu-id="4cc71-111">Runtime</span></span>|
|<span data-ttu-id="4cc71-112">Betroffene APIs</span><span class="sxs-lookup"><span data-stu-id="4cc71-112">Affected APIs</span></span>|<ul><li><xref:System.Web.SessionState.SessionStateMode.StateServer?displayProperty=nameWithType></li></ul>|
