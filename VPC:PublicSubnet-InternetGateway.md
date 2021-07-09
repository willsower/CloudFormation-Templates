# VPC With a Subnet -> InternetGateway

This template creates a VPC that has a public subnet within. The subnet is connected to the Internet Gateway using the RouteTable and Route. The image can be seen below.

![VPCSubnet:InternetGateway]()
## Template:
```YAML
AWSTemplateFormatVersion: 2010-09-09
Metadata:
  'AWS::CloudFormation::Designer':
    1731439e-5271-4392-989d-c5f3b77b813b:
      size:
        width: 520
        height: 210
      position:
        x: 90
        'y': 70
      z: 0
      embeds:
        - 72db1cab-ce84-4db2-a96a-3c38fa2a8066
    72db1cab-ce84-4db2-a96a-3c38fa2a8066:
      size:
        width: 470
        height: 150
      position:
        x: 120
        'y': 110
      z: 1
      parent: 1731439e-5271-4392-989d-c5f3b77b813b
      embeds:
        - f63dd2e9-a17d-41f7-9553-cec901789514
      iscontainedinside:
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
        - 1731439e-5271-4392-989d-c5f3b77b813b
    5421e7e2-c204-42a5-b678-ae312882df20:
      size:
        width: 60
        height: 60
      position:
        x: 220
        'y': -30
      z: 0
      embeds: []
    ea488b4a-cca6-484f-86a9-061e9e73253c:
      source:
        id: 1731439e-5271-4392-989d-c5f3b77b813b
      target:
        id: 5421e7e2-c204-42a5-b678-ae312882df20
      z: 0
    f63dd2e9-a17d-41f7-9553-cec901789514:
      size:
        width: 120
        height: 100
      position:
        x: 450
        'y': 140
      z: 2
      parent: 72db1cab-ce84-4db2-a96a-3c38fa2a8066
      embeds:
        - 1faaf9f6-52e0-4c14-9409-3336f511f617
      iscontainedinside:
        - 1731439e-5271-4392-989d-c5f3b77b813b
    04fd3415-097a-475d-9827-84af08db4a78:
      source:
        id: f63dd2e9-a17d-41f7-9553-cec901789514
      target:
        id: 72db1cab-ce84-4db2-a96a-3c38fa2a8066
      z: 3
    a352a927-fa78-4da6-82d8-c102fbbaec8a:
      source:
        id: f63dd2e9-a17d-41f7-9553-cec901789514
      target:
        id: 1731439e-5271-4392-989d-c5f3b77b813b
      z: 5
    1faaf9f6-52e0-4c14-9409-3336f511f617:
      size:
        width: 60
        height: 60
      position:
        x: 480
        'y': 170
      z: 3
      parent: f63dd2e9-a17d-41f7-9553-cec901789514
      isassociatedwith:
        - 5421e7e2-c204-42a5-b678-ae312882df20
      iscontainedinside:
        - f63dd2e9-a17d-41f7-9553-cec901789514
      dependson:
        - 1731439e-5271-4392-989d-c5f3b77b813b
    3dd2d05f-25b2-4d0e-9cf0-961f61c4a609:
      source:
        id: 1faaf9f6-52e0-4c14-9409-3336f511f617
      target:
        id: 1731439e-5271-4392-989d-c5f3b77b813b
      z: 4
    80a1c3a8-6aa9-4a99-8428-73899cf3bf53:
      source:
        id: 1faaf9f6-52e0-4c14-9409-3336f511f617
      target:
        id: 5421e7e2-c204-42a5-b678-ae312882df20
      z: 5
Resources:
  EC2VPC:
    Type: 'AWS::EC2::VPC'
    Properties:
      CidrBlock: 10.0.0.0/16
      EnableDnsSupport: 'true'
      EnableDnsHostnames: 'true'
    Metadata:
      'AWS::CloudFormation::Designer':
        id: 1731439e-5271-4392-989d-c5f3b77b813b
  EC2Subnet:
    Type: 'AWS::EC2::Subnet'
    Properties:
      VpcId: !Ref EC2VPC
      CidrBlock: 10.0.0.0/24
      AvailabilityZone: us-east-1a
    Metadata:
      'AWS::CloudFormation::Designer':
        id: 72db1cab-ce84-4db2-a96a-3c38fa2a8066
  EC2InternetGateway:
    Type: 'AWS::EC2::InternetGateway'
    Properties: {}
    Metadata:
      'AWS::CloudFormation::Designer':
        id: 5421e7e2-c204-42a5-b678-ae312882df20
  EC2VPCG3DAR3:
    Type: 'AWS::EC2::VPCGatewayAttachment'
    Properties:
      InternetGatewayId: !Ref EC2InternetGateway
      VpcId: !Ref EC2VPC
    Metadata:
      'AWS::CloudFormation::Designer':
        id: ea488b4a-cca6-484f-86a9-061e9e73253c
  EC2RouteTable:
    Type: 'AWS::EC2::RouteTable'
    Properties:
      VpcId: !Ref EC2VPC
    Metadata:
      'AWS::CloudFormation::Designer':
        id: f63dd2e9-a17d-41f7-9553-cec901789514
  EC2SRTA48521:
    Type: 'AWS::EC2::SubnetRouteTableAssociation'
    Properties:
      RouteTableId: !Ref EC2RouteTable
      SubnetId: !Ref EC2Subnet
    Metadata:
      'AWS::CloudFormation::Designer':
        id: 04fd3415-097a-475d-9827-84af08db4a78
  EC2Route:
    Type: 'AWS::EC2::Route'
    Properties:
      RouteTableId: !Ref EC2RouteTable
      GatewayId: !Ref EC2InternetGateway
      DestinationCidrBlock: 0.0.0.0/0
    Metadata:
      'AWS::CloudFormation::Designer':
        id: 1faaf9f6-52e0-4c14-9409-3336f511f617
    DependsOn:
      - EC2VPC
```
