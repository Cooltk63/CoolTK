</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="214" y="240" width="58" height="40" uuid="ab869773-7848-41ec-a345-1065bd655d24">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv4})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="214" y="280" width="58" height="40" uuid="0aad40c1-4910-40d8-a404-bb2cebd9a7b8">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)).add($V{LessALDProv4}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="98" y="360" width="58" height="40" uuid="648f0eec-fb44-4917-9b6b-e37391ad3876">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum2}.add($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.##-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="562" y="280" width="58" height="40" uuid="469e5262-0f87-4d8a-86cb-6284399b0ac6">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{LessALDProv10}==null ? new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100))) :
new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)).add($V{LessALDProv10}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="156" y="240" width="58" height="40" uuid="ca4e3315-d27f-4f46-bcb8-41071344aad4">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv3})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Column" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="214" y="320" width="58" height="40" uuid="73165b4b-d51a-4082-942b-019f8d1246e8">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum4}.add($V{IBGSum4}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="0" y="200" width="40" height="40" uuid="7c1a63ae-7e51-4f66-84c0-e3987633b4d3">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="pixel"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["Prov for IBG"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="620" y="200" width="58" height="40" uuid="77460750-1ebe-4f78-8627-825335d8cd95">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum11}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="214" y="200" width="58" height="40" uuid="a8fe4381-41c6-49f0-a334-0989eabfeeed">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="0" y="240" width="40" height="40" uuid="63cbc9bb-c6ba-4a41-9ace-c6e4b717af01">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="pixel"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["Less already provided inIBG"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="562" y="320" width="58" height="40" uuid="3e56c1d4-7ef6-42fe-90c3-4bc6ed72fc57">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum10}.add($V{IBGSum10}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="504" y="240" width="58" height="40" uuid="72f469d3-f320-4c0a-b909-3ce7881c91b9">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv9})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="#,##,###.##" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="98" y="280" width="58" height="40" uuid="8d1603cf-c4e8-4951-875e-6b4112d2d171">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{LessALDProv2}==null ? new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))) :
new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)).add($V{LessALDProv2}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="330" y="240" width="58" height="40" uuid="4af374bc-8928-4e27-b814-ed434597bc10">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv6})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.##-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="156" y="280" width="58" height="40" uuid="6bafbe42-e17b-4268-96ae-f3895d40b11c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{LessALDProv3}==null ? new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))) :
new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)).add($V{LessALDProv3}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="330" y="200" width="58" height="40" uuid="f1740fe7-58c5-48ee-8e4c-3eccde80fce4">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum6}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Auto" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="330" y="320" width="58" height="40" uuid="45ca1b5b-97f3-4e66-a678-6db230c387ca">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum6}.add($V{IBGSum6}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="40" y="200" width="58" height="40" uuid="f7e22c0c-8a3b-4002-b058-b1b30be25a32">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum1}.multiply( new BigDecimal(0.25) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="98" y="240" width="58" height="40" uuid="1e5bc7ef-7f90-4c39-97f5-9757fc074b26">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv2})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="272" y="240" width="58" height="40" uuid="b5705a1e-b083-44a8-a64c-9ea222956007">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv5})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="272" y="280" width="58" height="40" uuid="a0258900-e6fe-4a93-af46-fb4cf1fc64f2">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum5}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)).add($V{LessALDProv5}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="562" y="200" width="58" height="40" uuid="189ddcba-c3e3-4680-8e35-e8ccaa499fb5">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="504" y="280" width="58" height="40" uuid="1f49153e-f013-4490-9012-f2f10711b9f2">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum9}.multiply( new BigDecimal(0.75) ).divide(new BigDecimal(100)).add($V{LessALDProv9}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="388" y="280" width="58" height="40" uuid="07849a08-cbe8-4bbc-9664-fbc30ebe1470">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum7}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)).add($V{LessALDProv7}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="620" y="320" width="58" height="40" uuid="5e6ef2cf-7941-4ca6-b200-a9c7eb75901a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum11}.add($V{IBGSum11}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="1026" y="240" width="66" height="40" uuid="dc46280b-ae03-4bcd-98db-835f40dafe10">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv1}.add($V{LessALDProv2}).add($V{LessALDProv3}).add($V{LessALDProv4}).add($V{LessALDProv5}).add($V{LessALDProv6}).add($V{LessALDProv7}).add($V{LessALDProv8}).add($V{LessALDProv9}).add($V{LessALDProv10}).add($V{LessALDProv11}).add($V{LessALDProv17}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="156" y="200" width="58" height="40" uuid="f636581a-7f3e-49d1-9153-835447d59890">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="562" y="240" width="58" height="40" uuid="cb764a33-30d7-4304-aa42-84eb45b97a6b">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv10})]]></textFieldExpression>
			</textField>
			<componentElement>
				<reportElement x="1093" y="40" width="58" height="40" uuid="96e1975e-7474-44eb-a9ea-2afd0f5c978a"/>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="YSA" uuid="07f4f9d9-cfb7-4e2a-ad77-043a9f4af5df">
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="YSASUM" toVariable="LessFdCreditSum12"/>
					</datasetRun>
					<jr:listContents height="40" width="58"/>
				</jr:list>
			</componentElement>
			<componentElement>
				<reportElement x="1093" y="160" width="58" height="40" uuid="58812269-9e6e-4bd2-80ad-7aa83776aeef">
					<property name="com.jaspersoft.studio.layout"/>
				</reportElement>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="IBGSET" uuid="cbb7e633-b4ad-4a69-ad26-7f0dd97d7e72">
						<datasetParameter name="DATE">
							<datasetParameterExpression><![CDATA[$P{DATE}]]></datasetParameterExpression>
						</datasetParameter>
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="Sum1" toVariable="IBGSum1"/>
						<returnValue fromVariable="Sum2" toVariable="IBGSum2"/>
						<returnValue fromVariable="Sum3" toVariable="IBGSum3"/>
						<returnValue fromVariable="Sum4" toVariable="IBGSum4"/>
						<returnValue fromVariable="Sum5" toVariable="IBGSum5"/>
						<returnValue fromVariable="Sum6" toVariable="IBGSum6"/>
						<returnValue fromVariable="Sum7" toVariable="IBGSum7"/>
						<returnValue fromVariable="Sum8" toVariable="IBGSum8"/>
						<returnValue fromVariable="Sum9" toVariable="IBGSum9"/>
						<returnValue fromVariable="Sum10" toVariable="IBGSum10"/>
						<returnValue fromVariable="Sum11" toVariable="IBGSum11"/>
						<returnValue fromVariable="Sum12" toVariable="IBGSum12"/>
						<returnValue fromVariable="Sum13" toVariable="IBGSum13"/>
						<returnValue fromVariable="Sum14" toVariable="IBGSum14"/>
						<returnValue fromVariable="Sum15" toVariable="IBGSum15"/>
						<returnValue fromVariable="Sum16" toVariable="IBGSum16"/>
						<returnValue fromVariable="Sum17" toVariable="IBGSum17"/>
						<returnValue fromVariable="Sum18" toVariable="IBGSum18"/>
					</datasetRun>
					<jr:listContents height="40" width="58"/>
				</jr:list>
			</componentElement>
			<componentElement>
				<reportElement stretchType="ElementGroupHeight" x="1093" y="240" width="58" height="40" uuid="592a3fed-3e64-4300-8c83-a02706cf0f56">
					<property name="com.jaspersoft.studio.layout" value="com.jaspersoft.studio.editor.layout.FreeLayout"/>
				</reportElement>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="LessAlredyProvided" uuid="5ed11107-f6e8-4577-b5c1-3bcaa99f6943">
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="LAP18" toVariable="LessALDProv18"/>
						<returnValue fromVariable="LAP17" toVariable="LessALDProv17"/>
						<returnValue fromVariable="LAP16" toVariable="LessALDProv16"/>
						<returnValue fromVariable="LAP15" toVariable="LessALDProv15"/>
						<returnValue fromVariable="LAP14" toVariable="LessALDProv14"/>
						<returnValue fromVariable="LAP13" toVariable="LessALDProv13"/>
						<returnValue fromVariable="LAP12" toVariable="LessALDProv12"/>
						<returnValue fromVariable="LAP11" toVariable="LessALDProv11"/>
						<returnValue fromVariable="LAP10" toVariable="LessALDProv10"/>
						<returnValue fromVariable="LAP9" toVariable="LessALDProv9"/>
						<returnValue fromVariable="LAP8" toVariable="LessALDProv8"/>
						<returnValue fromVariable="LAP7" toVariable="LessALDProv7"/>
						<returnValue fromVariable="LAP6" toVariable="LessALDProv6"/>
						<returnValue fromVariable="LAP5" toVariable="LessALDProv5"/>
						<returnValue fromVariable="LAP4" toVariable="LessALDProv4"/>
						<returnValue fromVariable="LAP3" toVariable="LessALDProv3"/>
						<returnValue fromVariable="LAP2" toVariable="LessALDProv2"/>
						<returnValue fromVariable="LAP1" toVariable="LessALDProv1"/>
					</datasetRun>
					<jr:listContents height="40" width="58"/>
				</jr:list>
			</componentElement>
			<textField evaluationTime="Report" isBlankWhenNull="true">
				<reportElement x="1026" y="700" width="66" height="30" uuid="7441a6a7-3f39-485b-9f26-9d84505a154c">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{InputList3_10})]]></textFieldExpression>
			</textField>
			<textField evaluationTime="Report" isBlankWhenNull="true">
				<reportElement x="1026" y="730" width="66" height="30" uuid="0b82249c-3473-43d6-b926-9d54b2ca90cd">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8" isBold="true"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{InputList3_10} == null  || $V{InputListSum1}==null ? new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{ProvDomAdvSum1}.add($V{ProvDomAdvSum2}).add($V{ProvDomAdvSum3}).add($V{ProvDomAdvSum4}).add($V{ProvDomAdvSum5}).add($V{ProvDomAdvSum6}).add($V{ProvDomAdvSum7}).add($V{ProvDomAdvSum8}).add($V{ProvDomAdvSum9}).add($V{ProvDomAdvSum10}).add($V{ProvDomAdvSum11}).add($V{DomOffSum12}.subtract($V{LessFdCreditSum12}).multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{IBGSum1}.multiply( new BigDecimal(0.25) ).divide(new BigDecimal(100)).add($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum5}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum6}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum7}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum8}.multiply( new BigDecimal(10) ).divide(new BigDecimal(100)))
        .add($V{IBGSum9}.multiply( new BigDecimal(0.75) ).divide(new BigDecimal(100)))
        .add($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)))
        .add($V{IBGSum11}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum12}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{LessALDProv18}))) :

new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{ProvDomAdvSum1}.add($V{ProvDomAdvSum2}).add($V{ProvDomAdvSum3}).add($V{ProvDomAdvSum4}).add($V{ProvDomAdvSum5}).add($V{ProvDomAdvSum6}).add($V{ProvDomAdvSum7}).add($V{ProvDomAdvSum8}).add($V{ProvDomAdvSum9}).add($V{ProvDomAdvSum10}).add($V{ProvDomAdvSum11}).add($V{DomOffSum12}.subtract($V{LessFdCreditSum12}).multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{IBGSum1}.multiply( new BigDecimal(0.25) ).divide(new BigDecimal(100)).add($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum5}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum6}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum7}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum8}.multiply( new BigDecimal(10) ).divide(new BigDecimal(100)))
        .add($V{IBGSum9}.multiply( new BigDecimal(0.75) ).divide(new BigDecimal(100)))
        .add($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)))
        .add($V{IBGSum11}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum12}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{LessALDProv18})).add($V{InputListSum1}).subtract($V{InputList3_10}))]]></textFieldExpression>
			</textField>
			<textField evaluationTime="Report" isBlankWhenNull="true">
				<reportElement x="1026" y="760" width="66" height="30" uuid="ab3028aa-8c6d-4bb8-b08c-cfbfdad7f78d">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8" isBold="true"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{InputListSum1} == null ?new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{ProvDomAdvSum1}.add($V{ProvDomAdvSum2}).add($V{ProvDomAdvSum3}).add($V{ProvDomAdvSum4}).add($V{ProvDomAdvSum5}).add($V{ProvDomAdvSum6}).add($V{ProvDomAdvSum7}).add($V{ProvDomAdvSum8}).add($V{ProvDomAdvSum9}).add($V{ProvDomAdvSum10}).add($V{ProvDomAdvSum11}).add($V{DomOffSum12}.subtract($V{LessFdCreditSum12}).multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{IBGSum1}.multiply( new BigDecimal(0.25) ).divide(new BigDecimal(100)).add($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum5}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum6}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum7}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum8}.multiply( new BigDecimal(10) ).divide(new BigDecimal(100)))
        .add($V{IBGSum9}.multiply( new BigDecimal(0.75) ).divide(new BigDecimal(100)))
        .add($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)))
        .add($V{IBGSum11}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum12}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{LessALDProv18}))) :

new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{ProvDomAdvSum1}.add($V{ProvDomAdvSum2}).add($V{ProvDomAdvSum3}).add($V{ProvDomAdvSum4}).add($V{ProvDomAdvSum5}).add($V{ProvDomAdvSum6}).add($V{ProvDomAdvSum7}).add($V{ProvDomAdvSum8}).add($V{ProvDomAdvSum9}).add($V{ProvDomAdvSum10}).add($V{ProvDomAdvSum11}).add($V{DomOffSum12}.subtract($V{LessFdCreditSum12}).multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{IBGSum1}.multiply( new BigDecimal(0.25) ).divide(new BigDecimal(100)).add($V{IBGSum2}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum3}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum4}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum5}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum6}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum7}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))
        .add($V{IBGSum8}.multiply( new BigDecimal(10) ).divide(new BigDecimal(100)))
        .add($V{IBGSum9}.multiply( new BigDecimal(0.75) ).divide(new BigDecimal(100)))
        .add($V{IBGSum10}.multiply( new BigDecimal(1) ).divide(new BigDecimal(100)))
        .add($V{IBGSum11}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))
        .add($V{IBGSum12}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))).add($V{LessALDProv18})).add($V{InputListSum1}).subtract($V{InputList2_9}))]]></textFieldExpression>
			</textField>
			<componentElement>
				<reportElement x="1026" y="400" width="66" height="30" uuid="d1ea631f-70dc-4186-bec4-647e4aeb6484">
					<property name="com.jaspersoft.studio.layout" value="com.jaspersoft.studio.editor.layout.VerticalRowLayout"/>
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
				</reportElement>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="INPUTLIST1" uuid="1fd44258-da21-463c-9aaf-9b182f6308ad">
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="InputListCAL1" toVariable="InputListSum1"/>
					</datasetRun>
					<jr:listContents height="30" width="66">
						<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
							<reportElement stretchType="ElementGroupHeight" x="0" y="0" width="66" height="30" uuid="5aa459e4-b709-4ddf-a6b2-a8425488c45c">
								<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
								<property name="com.jaspersoft.studio.unit.width" value="px"/>
							</reportElement>
							<box>
								<pen lineWidth="1.0" lineStyle="Solid"/>
								<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
								<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
								<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
								<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
							</box>
							<textElement textAlignment="Right" verticalAlignment="Middle">
								<font size="8"/>
								<paragraph rightIndent="2"/>
							</textElement>
							<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($F{ANX2C_TOT})]]></textFieldExpression>
						</textField>
					</jr:listContents>
				</jr:list>
			</componentElement>
			<componentElement>
				<reportElement x="1092" y="670" width="51" height="30" uuid="1593053a-28c3-4fdb-896e-9ceb387a069e"/>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="INPUTLIST2" uuid="e94bc615-1a90-4f30-82f3-0b5dd011421b">
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="InputList9" toVariable="InputList2_9"/>
					</datasetRun>
					<jr:listContents height="30" width="51"/>
				</jr:list>
			</componentElement>
			<componentElement>
				<reportElement x="1092" y="700" width="51" height="30" uuid="bbcec194-dfe4-444b-8240-51af5e931bed"/>
				<jr:list xmlns:jr="http://jasperreports.sourceforge.net/jasperreports/components" xsi:schemaLocation="http://jasperreports.sourceforge.net/jasperreports/components http://jasperreports.sourceforge.net/xsd/components.xsd" printOrder="Vertical">
					<datasetRun subDataset="INPUTLIST3" uuid="cc2b5d39-4987-4ddf-8310-99a586c50c72">
						<connectionExpression><![CDATA[$P{REPORT_CONNECTION}]]></connectionExpression>
						<returnValue fromVariable="InputList3" toVariable="InputList3_10"/>
					</datasetRun>
					<jr:listContents height="30" width="51"/>
				</jr:list>
			</componentElement>
			<textField>
				<reportElement x="0" y="400" width="1026" height="30" uuid="4eed3c1d-fc26-44bd-9625-67f67cec1571">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Add : Provision required for Derivative exposure (GMU) as on  "+$P{DATE} +" as on "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="430" width="1026" height="30" uuid="79fb4d3b-e3e2-4f95-a6b0-92995b59b0a4">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Provision required for Derivative exposure (FO) " +$P{DATE} +" as on "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="460" width="1026" height="30" uuid="39f4f24f-e9e4-48ef-9bd9-e6f7fc16ee13">
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Add Unhedged Foreign currency Exposure  provision " +$P{DATE} +" as on "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="490" width="1026" height="30" uuid="f47de13d-2f3f-42cb-9afd-9ae0e9a1ef02">
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["CAG MCG SPECIFIC ACCOUNT PROVISION " +$P{DATE} +" AS ON "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="520" width="1026" height="30" uuid="a9051e5e-dffc-45dc-af6e-dd9a80555220">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA[" Add: CIF LEVEL Rest Provision"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="550" width="1026" height="30" uuid="23fb03be-0906-4859-857d-06aabb6fc640">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["DCCO"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="580" width="1026" height="30" uuid="095ee7f7-2109-4288-8a84-0cd8f27ab5ed">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["REHBU Restd+ Other prov"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="610" width="1026" height="30" uuid="399a2d91-0a14-4c90-abaf-861613aae963">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Rest Agri Std Provision  "+$P{DATE} +" as on "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="640" width="1026" height="30" uuid="822354a4-878a-42d7-a361-aebd45cd8bb4">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font isBold="true"/>
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Total Provision on STD assets "+$P{DATE} +" as on "+(new BigDecimal($P{DATE}.substring(6,10)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="670" width="1026" height="30" uuid="c9ddd407-1153-4e7f-90ee-ac1f87681662">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Total Provisions on Standard Assets as on "+
IF($P{DATE}.substring( 3, 5).equalsIgnoreCase( "06" ), "31.03."+$P{DATE}.substring(6, 10),
IF($P{DATE}.substring( 3, 5 ).equalsIgnoreCase( "09" ), "30.06."+$P{DATE}.substring(6, 10),
IF($P{DATE}.substring( 3, 5 ).equalsIgnoreCase( "12" ), "30.09."+$P{DATE}.substring(6, 10) ,
"31.12."+(INTEGER_VALUE($P{DATE}.substring(6, 10))-1))))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="700" width="1026" height="30" uuid="2f7682f8-59d9-4616-a138-c0cc94d683e7">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Total Provisions on Standard Assets "+(new BigDecimal($P{DATE}.substring(6,10)).subtract(new BigDecimal(1)))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="730" width="1026" height="30" uuid="afe57178-7709-4154-bb9b-e64ced582a0a">
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font isBold="true"/>
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Additional Provision Required 12 Months FY  "+(new BigDecimal($P{DATE}.substring(6,10)).subtract(new BigDecimal(1))) +"-" +($P{DATE}.substring(8,10))]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="760" width="1026" height="30" uuid="03835bf0-64f2-4f81-81bd-aca4e70da087">
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font isBold="true"/>
					<paragraph rightIndent="5"/>
				</textElement>
				<textFieldExpression><![CDATA["Additional Provision Required 3 Months FY " +(new BigDecimal($P{DATE}.substring(6,10)).subtract(new BigDecimal(1))) +"-" +($P{DATE}.substring(8,10)) +" "+($P{DATE}.substring(6,10)) + "Q1/2/3/4"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="0" width="58" height="40" uuid="0d59f308-1670-4057-866b-464e7af65914">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum12})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="0" width="58" height="40" uuid="3881b60e-179c-4c84-86ed-c0592f2fc501">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum13})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="0" width="58" height="40" uuid="07757c96-d1f4-4314-96ed-2a0e903ead04">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum14})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="0" width="58" height="40" uuid="63308fba-ed8c-4f3a-b194-ba83dbeb45e2">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum15})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="0" width="58" height="40" uuid="fbfce26e-bcb6-4672-bf28-d0975d718477">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum16})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="40" width="58" height="40" uuid="aeb4cac8-d612-4423-990e-2d245bb39ec4">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="40" width="58" height="40" uuid="392ad332-0c94-4bed-b59f-a62dda651692">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="40" width="58" height="40" uuid="56d682a6-bee9-4e1d-9c19-f8f4d663b542">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="40" width="58" height="40" uuid="745553ee-2fde-4163-ae83-6d5ae66a2da9">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="40" width="58" height="40" uuid="4d696fa8-027e-4883-90f6-bb9780b0331f">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="80" width="58" height="40" uuid="8d5986c8-526b-4242-8643-af151efe1c7a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum12})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="80" width="58" height="40" uuid="7bb2d5d5-912c-4bdc-8fec-49dc75b2286a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum13})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="80" width="58" height="40" uuid="d91cc4aa-9d52-4476-95c4-bafa61f26b89">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum14})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="80" width="58" height="40" uuid="bd6311e0-f320-4307-a0f6-54375ecff5b9">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum15})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="80" width="58" height="40" uuid="62fd9f2f-3b20-4176-be22-7278b884dfb5">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum16})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="#,##,###0.##;(#,##,###0.##-)">
				<reportElement stretchType="ElementGroupHeight" x="678" y="120" width="58" height="40" uuid="bab13cd7-2531-46e4-aaf8-e33ad8f6ad26">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{DomOffSum12}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="#,##,###0.##;(#,##,###0.##-)">
				<reportElement stretchType="ElementGroupHeight" x="736" y="120" width="58" height="40" uuid="90a61dbf-9b42-4298-989c-b9bd767764b6">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{DomOffSum13}.multiply( new BigDecimal(40) ).divide(new BigDecimal(100))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="#,##,###0.##;(#,##,###0.##-)">
				<reportElement stretchType="ElementGroupHeight" x="794" y="120" width="58" height="40" uuid="dddfdd75-49cb-4cb8-89e4-46877a5fe553">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{DomOffSum14}.multiply( new BigDecimal(40) ).divide(new BigDecimal(100))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="#,##,###0.##;(#,##,###0.##-)">
				<reportElement stretchType="ElementGroupHeight" x="852" y="120" width="58" height="40" uuid="aa93273c-9d9b-4148-a0e5-b86b1369919c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{DomOffSum15}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" pattern="#,##,###0.##;(#,##,###0.##-)">
				<reportElement stretchType="ElementGroupHeight" x="910" y="120" width="58" height="40" uuid="e89d692e-2f32-46a7-b665-0d47f0647a55">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{DomOffSum16}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="160" width="58" height="40" uuid="099f3bba-e248-44df-8395-d2700ce8828c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum12})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="160" width="58" height="40" uuid="ff0f5ab8-8030-48fe-95d0-74c989ced00d">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum13})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="160" width="58" height="40" uuid="70525869-b3ac-4959-94b0-4f04da3d1075">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum14})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="160" width="58" height="40" uuid="447932db-0306-43be-be5e-b5a3d577bf43">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum15})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="160" width="58" height="40" uuid="339d5249-dfaa-482f-9a15-13fa5003c04a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum16})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="200" width="58" height="40" uuid="f2cd2ba5-9590-48b2-9e7e-b8bbfb9fabc0">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum12}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="200" width="58" height="40" uuid="8d609cae-879d-4c51-aa4e-78212bf1d50c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum13}.multiply( new BigDecimal (15).divide(new BigDecimal(100))))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="200" width="58" height="40" uuid="84f2fd62-7573-4f0f-9469-794c272f4095">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum14}.multiply( new BigDecimal(40) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="200" width="58" height="40" uuid="92d3c481-ce85-4a0e-9f3d-1df851cf9564">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum15}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="200" width="58" height="40" uuid="5dbf2754-32db-4b72-8cc3-c8156ca9bcdf">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum16}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="240" width="58" height="40" uuid="1a86aa1b-f70d-42ce-880b-6b7783abe039">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv12})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="240" width="58" height="40" uuid="e3bd45d9-7c2b-49ac-be27-d8adad59a0f8">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv13})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="240" width="58" height="40" uuid="c0910231-0300-43de-a6d1-dadd157d0b4a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv14})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="240" width="58" height="40" uuid="c7de99a7-0a33-4358-88d9-28d67a0044a3">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv15})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="240" width="58" height="40" uuid="71115b0e-ecb4-4a2f-8a83-97bd8b919144">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="0.0"/>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{LessALDProv16})]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="280" width="58" height="40" uuid="60f643d0-8acd-4ff2-a001-09fc5fad8652">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum12}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)).add($V{LessALDProv12}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="280" width="58" height="40" uuid="96fb5719-6266-4964-82ba-3fa771ae9ec0">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum13}.multiply( new BigDecimal(15) ).divide(new BigDecimal(100)).add($V{LessALDProv13}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="280" width="58" height="40" uuid="c9b0e1f5-724c-4c29-96ce-11998328d727">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format( 
 	($V{IBGSum14}.multiply(new BigDecimal(40).divide(new BigDecimal(100))).add($V{LessALDProv14}))
 )]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="280" width="58" height="40" uuid="db39b642-ada6-4d54-a878-1104426205be">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format(($V{IBGSum15}.multiply( new BigDecimal(5) ).divide(new BigDecimal(100)).add($V{LessALDProv15})))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Report" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="280" width="58" height="40" uuid="6b6c1abf-390e-4781-ad37-f8b916f0e918">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{IBGSum16}.multiply( new BigDecimal(0.4) ).divide(new BigDecimal(100)).add($V{LessALDProv16}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="320" width="58" height="40" uuid="4c48b1d5-89e1-49fd-9ede-91eb5fbb6f0c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum12}.add($V{IBGSum12}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="320" width="58" height="40" uuid="863a07d9-a5b1-472d-9cba-9cbdc0ed6d6b">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum13}.add($V{IBGSum13}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="320" width="58" height="40" uuid="f4faacfe-0203-4d87-97e0-1df7aae138f4">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum14}.add($V{IBGSum14}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="320" width="58" height="40" uuid="c64e8028-1485-483b-9f02-d492a8e70117">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum15}.add($V{IBGSum15}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="320" width="58" height="40" uuid="4602ff9d-e941-4f82-8f0f-05ae5f14e586">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="1"/>
				</textElement>
				<textFieldExpression><![CDATA[new com.ibm.icu.text.DecimalFormat("#,##,##0.00").format($V{DomOffSum16}.add($V{IBGSum16}))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="678" y="360" width="58" height="40" uuid="587b730b-87cd-49a2-819f-4a997d233715">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum12}.add($V{IBGSum12}.multiply( new BigDecimal(5)).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="736" y="360" width="58" height="40" uuid="6ce66a28-6b94-46b7-a4e2-9fcf9fd33605">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum13}.add($V{IBGSum13}.multiply( new BigDecimal(15)).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="794" y="360" width="58" height="40" uuid="facce7d9-72cd-4527-b601-b80aa4739939">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum14}.add($V{IBGSum14}.multiply( new BigDecimal(40)).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="852" y="360" width="58" height="40" uuid="a81a5087-89cb-495c-9947-746e9126e19c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum15}.add($V{IBGSum15}.multiply( new BigDecimal(5)).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band" pattern="###0.###;(###0.###-)" isBlankWhenNull="true">
				<reportElement stretchType="ElementGroupHeight" x="910" y="360" width="58" height="40" uuid="8088cf1a-fd78-452c-a3ed-90adc1d362df">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Right" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph rightIndent="2"/>
				</textElement>
				<textFieldExpression><![CDATA[$V{ProvDomAdvSum16}.add($V{IBGSum16}.multiply( new BigDecimal(0.4)).divide(new BigDecimal(100)))]]></textFieldExpression>
			</textField>
		</band>
	</summary>
	<noData>
		<band height="270">
			<textField>
				<reportElement x="0" y="15" width="1092" height="20" uuid="cef29f23-6a99-4545-8b54-4216b70c1d9c"/>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["ANNEX-2C"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="35" width="1092" height="20" uuid="c5ec066a-ab01-46b6-9180-fac3c62d02c9"/>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["STATEMENT OF ADDITIONAL PROVISIONING REQUIREMENT FOR STANDARD ASSETS"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="0" y="55" width="1092" height="20" uuid="53f6034f-36c4-4072-8595-506c4304babe"/>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["POSITION AS ON "+$P{DATE}]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="504" y="75" width="174" height="20" uuid="a12fd9e8-d222-4ad2-9ffb-6ca1981655fe">
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["EXP. TO REAL ESTATE"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="98" y="155" width="58" height="20" uuid="f0311a3d-34f1-4787-b5b7-81e35bba91d9">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["2"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="968" y="75" width="58" height="80" uuid="da52c738-750d-4afe-8370-e6fb4adfd1fa">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["ALL OTHERS      (0.40%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="562" y="95" width="58" height="60" uuid="ff5ae5a7-5a16-4949-96f2-4de96d02a19a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["EXP. TO COMM REAL ESTATE               (1.0%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="40" y="155" width="58" height="20" uuid="e2f04f0d-bad4-4b85-a58b-a0c98632bdd5">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["1"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="968" y="155" width="58" height="20" uuid="02da9d64-37d4-4f55-8c36-abc2b8bc787a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["11"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="98" y="95" width="58" height="60" uuid="6a87dea5-1038-45f9-b80d-b18e58e52a4f">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["PERSONAL  LOANS  NBFC-NDSL   (0.40%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="562" y="155" width="58" height="20" uuid="dd557ef1-286d-47c2-a3c1-9a1038a09b1e">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["9"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="98" y="75" width="348" height="20" uuid="6ec310c1-6c0f-4c8a-be53-6d2dde1daf65">
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["RESTURCTURED ACCOUNTS"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="388" y="155" width="58" height="20" uuid="e9517bc0-cc20-441b-a1e0-0074f861f0a0">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["7"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="446" y="95" width="58" height="60" uuid="b5445749-87ee-4148-8175-3802f2ea1727">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["Covid"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="214" y="155" width="58" height="20" uuid="7462cdc6-3391-4069-b30c-8899cd5fc25a">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["4"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="0" y="75" width="40" height="100" uuid="c6c7df87-fbae-4f83-94b6-9f0f318b6eb7">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["CIRCLES"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="1026" y="75" width="66" height="80" uuid="81f43b53-a374-4a9c-97fc-4a4b4d3ae1ce">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["TOTAL"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="156" y="95" width="58" height="60" uuid="c9b27001-beab-4ea1-8053-39a037ef2bd9">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["EXPOSURE TO CAP MARKET        (0.40%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="504" y="155" width="58" height="20" uuid="2de5228b-63af-4b91-b2fe-75c8df452c14">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["8"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="330" y="95" width="58" height="60" uuid="7960b685-147f-4e2d-9386-3f8556431d42">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["NEW RESTRUTURED STANDARD A/CS (AFTER 01.06.2013)  (5.0%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="330" y="155" width="58" height="20" uuid="f90ed046-8f00-41b3-830e-9e147c89a036">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["6"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="214" y="95" width="58" height="60" uuid="2e0a5ee2-b888-4db0-9862-17ccaff00571">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["STANDARD                  (5.00%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="272" y="95" width="58" height="60" uuid="3f47269d-17f8-483d-a97d-8dda3f726f80">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["NPAs UPGRADED TO STANDARD ASSETS   (5.00%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="620" y="95" width="58" height="60" uuid="3b8bb2aa-7d0d-46c6-bf75-78463366821d">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["OTHERS                   (0.40%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="272" y="155" width="58" height="20" uuid="75d52a0b-dfa3-4d58-960d-8b7ce61f39ec">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["5"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="620" y="155" width="58" height="20" uuid="f8938048-02a7-425d-8156-f47c1adbcb65">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["10"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="156" y="155" width="58" height="20" uuid="1f5696b8-2621-403f-8158-0a7b5166c39e">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["3"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="504" y="95" width="58" height="60" uuid="b0cddf9b-4a14-45e9-acdd-28b6c34f3622">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["COMMERCIAL REAL ESTATE - RESIDENTIAL - HOUSING           (0.75%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="40" y="75" width="58" height="80" uuid="7a57731f-ccee-4da9-bdc0-cbddc350fae2">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["GENERAL                 (0.25%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="446" y="75" width="58" height="20" uuid="3350f5d8-3ade-47dc-a86f-74f8f4f39ea4">
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA[""]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="388" y="95" width="58" height="60" uuid="7898cd12-cfd1-4958-bfea-517192ca92c1">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["MEME Rest Standard Assets @5%"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="1026" y="155" width="66" height="20" uuid="cc46999e-48b5-41fb-98f1-35b58dc66bd0">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["12"]]></textFieldExpression>
			</textField>
			<staticText>
				<reportElement x="0" y="175" width="1092" height="45" uuid="a4c645e9-a507-4246-bfce-723f7ae28a28"/>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8" isBold="true"/>
				</textElement>
				<text><![CDATA[NO DATA  AVAILABLE]]></text>
			</staticText>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="852" y="155" width="58" height="20" uuid="be801476-6794-4b61-8113-3aac5b633965">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["15"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="678" y="75" width="58" height="80" uuid="500e4f45-b8a9-4d63-8251-20b01ece6d38">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["WILFUL DEFAULTER - Standard (5.0%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="736" y="95" width="58" height="60" uuid="30d7d420-d45d-4ba7-a0e4-d3242ca54dc5">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["Secured (15%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="910" y="155" width="58" height="20" uuid="4775d245-c88a-4f77-96c6-1e2914ab3169">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["16"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="678" y="155" width="58" height="20" uuid="ed0d1cd6-ec00-4cdb-8690-af2792e412be">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["12"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="852" y="75" width="116" height="20" uuid="cd80f49d-41f3-4489-badc-3ae878139dca">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["DCCO"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="852" y="95" width="58" height="60" uuid="ab0203b0-97d0-4216-8fca-2ed947475768">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["RESTRUCTURE ( 5.0 % )"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="794" y="95" width="58" height="60" uuid="e129fa2d-4890-48f0-82b1-aebad6321760">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Left" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="5" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["Unsecured            (40.0%)"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="794" y="155" width="58" height="20" uuid="34d6616c-0c46-473a-923d-fda0f8ab9a32">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["14"]]></textFieldExpression>
			</textField>
			<textField textAdjust="ScaleFont" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="910" y="95" width="58" height="60" uuid="f28fda83-ee45-4d17-aaa0-8285dcfef9fe">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.leftIndent" value="px"/>
					<property name="com.jaspersoft.studio.unit.rightIndent" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
					<paragraph leftIndent="10" rightIndent="10"/>
				</textElement>
				<textFieldExpression><![CDATA["NONRESTRUCTURE ( 0.40 % )"]]></textFieldExpression>
			</textField>
			<textField>
				<reportElement x="736" y="75" width="116" height="20" uuid="1ce8d146-c7f6-494d-8229-21a8f1d4bf86">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<topPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<leftPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<bottomPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
					<rightPen lineWidth="1.0" lineStyle="Solid" lineColor="#000000"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["NON COOPERATIVE BORROWER"]]></textFieldExpression>
			</textField>
			<textField textAdjust="StretchHeight" evaluationTime="Band">
				<reportElement stretchType="ElementGroupHeight" x="736" y="155" width="58" height="20" uuid="84893c75-f167-4412-be09-26b3393a652c">
					<property name="com.jaspersoft.studio.unit.width" value="px"/>
					<property name="com.jaspersoft.studio.unit.height" value="px"/>
				</reportElement>
				<box>
					<pen lineWidth="1.0"/>
				</box>
				<textElement textAlignment="Center" verticalAlignment="Middle">
					<font size="8"/>
				</textElement>
				<textFieldExpression><![CDATA["13"]]></textFieldExpression>
			</textField>
		</band>
	</noData>
</jasperReport>


This is the jasper code in circes columns on the row of "Net Provision held for FO in India" I am having issue my rows calculation wont show for some of cells shows data in cells are cell nos are 1,2,3,10,17 what is issue with my jasper & why i cant the the row data.
