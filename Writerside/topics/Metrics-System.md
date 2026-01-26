# Metrics System

* All of our plugins collect some basic non-sensitive information about your servers. They are used for statistical purposes and for deciding what versions should stay supported.
* Data is identified by a random UUID which is generated on the first server startup.
* **No data** is sent about your players, other plugins or other programs running on your machine.
* Both of the used systems can be disabled, read below to see how.

<tabs>
    <tab title="BStats">
        <h2 id="where-can-be-found-bstats">Where can the collected data be found?</h2>
        <a href="https://bstats.org/">bstats.org</a>
        <tip>
            BStats is not owned by us, so we suggest reading their own policies as information here might not be 100% accurate.
        </tip>
        <h2 id="collected-data-bstats">What data is collected?</h2>
        <list type="bullet">
            <li>Server Location (country where the server is located)</li>
            <li>Server Software (platform and version)</li>
            <li>Minecraft Version</li>
            <li>Server Online Mode (online or offline mode)</li>
            <li>Java Version</li>
            <li>Operating System Information (name, version, architecture)</li>
            <li>Server Hardware Information (cpu type, core count)</li>
            <li>Online Player Count</li>
        </list>
        <tip>
            You can find the source code for the system on <a href="https://github.com/Bastian/bStats">GitHub</a>!
        </tip>
        <h2 id="disable-bstats">How to disable?</h2>
        Go to the <code>plugins/bStats/config.yml</code> file and set the <code>enabled</code> setting to false. After this is completed, restart the server to apply the changes.
    </tab>
    <tab title="AxMetrics">
        <h2 id="where-can-be-found-axmetrics">Where can the collected data be found?</h2>
        <a href="https://www.artillex-studios.com/metrics">artillex-studios.com/metrics</a>
        <h2 id="collected-data-axmetrics">What data is collected?</h2>
        <list type="bullet">
            <li>Server Location (country where the server is located)</li>
            <li>Server Software (platform and version)</li>
            <li>Minecraft Version</li>
            <li>Server Online Mode (online or offline mode)</li>
            <li>Java Version</li>
            <li>Operating System Information (name, version, architecture)</li>
            <li>Server Hardware Information (cpu type, core count)</li>
            <li>Online Player Count</li>
        </list>
        <tip>
            You can find the source code for the system on <a href="https://github.com/Artillex-Studios/AxAPI/tree/master/api/src/main/java/com/artillexstudios/axapi/metrics">GitHub</a>!
        </tip>
        <h2 id="disable-axmetrics">How to disable?</h2>
        Go to the <code>plugins/AxAPI/metrics.yml</code> file and set the <code>enabled</code> setting to false. After this is completed, restart the server to apply the changes.
    </tab>
</tabs>