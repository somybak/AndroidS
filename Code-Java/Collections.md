String myName = "saesompark";
		String ahChim = "ahChim";
		String saetByul = "saetByul";
		String gaeMee = "gaeMee";
		String daSom = "daSom";
				
		//��ü�� ���� �ڵ�� ������� ��. ���� �ܰ迡 ����ȭ�� ������ ������ ����� �ǹ� 
		//-> �̰� �ڵ�� ���� �� Ŭ���� -> �����Ű�� ���� ��ǻ�� �� �ֱ����ġ�� �ö� �� instance ��ü
		
		int num = 57;
		
		ArrayList<String> nameList = new ArrayList<String>();
		//generic: ���ο� �߰��Ǵ� ��� ���� Ÿ���� ��������. <����> �ȿ� ���ϴ� Ÿ���� ��. 
		//ArrayList : �� �޸� ������ Ȯ���Ͽ� �ּ� ������ ���Ӹ���Ʈ�� �Ű���.
		
		//�Է��ϸ� �ϳ��ϳ� �׾���
		nameList.add(myName);
		nameList.add(ahChim);
		nameList.add(saetByul);
		nameList.add(gaeMee);
		nameList.add(daSom);
		
	//	System.out.println("2��°���="+nameList.get(0));
	// .get() : add�� �� ������� (��ȣ)��° �����͸� �����´�. 0���� ����  
	
//		//���ÿ� ����
//		int i=0;
//		int nameListsize = nameList.size(); 
//		for(i=0 ; i<nameListsize ; i++){
//			System.out.println(nameList.get(i));
//			//
//			//�ڵ� ǥ�� : �ݺ������� ���� �迭�� ������� ������� ����� �ǰ� ������ ����. int���� ���
//			//nameList.remove(2); ������ų ��� ������ �ٲ�Ƿ�..
//			
			
		//���� for��
		// nameList.add(new Integer(num));
		
		
		// for(Object name : nameList) {
			//String temp = item.toString();
			// System.out.println(item);
			// System.out.println(nameList.indexOf(item));
		// }
		// ':'�ݷ� - �����϶�� �ǹ�. �˾Ƽ� �ϳ��ϳ��� ������ ���� ���� ����.
		// for(String name : nameList) <= nameList�� add�ϸ鼭 Object������ �ٲ���.  