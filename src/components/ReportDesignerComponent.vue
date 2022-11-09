<template>
  <div
    ref="designer"
    style="position: absolute; left: 0; right: 0; top: 0; bottom: 0"
    data-bind="dxReportDesigner: $data"
  ></div>
</template>

<script>
import ko from "knockout";
import "devexpress-reporting";

export default {
  name: "ReportDesignerComponent",
  mounted() {
    var designerOptions = {
      reportUrl: ko.observable("Categories"), // The URL of a report that is opened in the Report Designer when the application starts.
      requestOptions: {
        host: "http://localhost:54114/",
        // Use this line for the ASP.NET MVC backend.
        getDesignerModelAction: "ReportDesigner/GetReportDesignerModel",
        // Uncomment this line if you use an ASP.NET Core backend.
        //invokeAction: "DXXRD"
      },
    };
    ko.applyBindings(designerOptions, this.$refs.designer);
  },
  beforeUnmount() {
    ko.cleanNode(this.$refs.designer);
  },
};
</script>
