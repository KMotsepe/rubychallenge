require 'tsort'

class AjlistNode 
	# Define the accessor and reader of class AjlistNode
	attr_reader :id, :next
	attr_accessor :id, :next
	#  Vertices node key
	def initialize(id) 
		#  Set value of node key
		self.id = id
		self.next = nil
	end

end

class Vertices 
	# Define the accessor and reader of class Vertices
	attr_reader :data, :next, :last
	attr_accessor :data, :next, :last
	def initialize(data) 
		self.data = data
		self.next = nil
		self.last = nil
	end

end

class Graph 
	# Define the accessor and reader of class Graph
	attr_reader :size, :node
	attr_accessor :size, :node
	#  Number of Vertices
	def initialize(size) 
		#  Set value
		self.size = size
		self.node = Array.new(size) {nil}
		self.setData()
	end

	#  Set initial node value
	def setData() 
		if (self.size <= 0) 
			print("\nEmpty Graph\n")
		else
 
			index = 0
			while (index < self.size) 
				#  Set initial node value
				self.node[index] = Vertices.new(index)
				index += 1
			end

		end

	end

	def connection(start, last) 
		#  Safe connection
		edge = AjlistNode.new(last)
		if (self.node[start].next == nil) 
			self.node[start].next = edge
		else
 
			#  Add edge at the end
			self.node[start].last.next = edge
		end

		#  Get last edge 
		self.node[start].last = edge
	end

	#   Handling the request of adding new edge
	def addEdge(start, last) 
		if (start >= 0 && start < self.size && 
            last >= 0 && last < self.size) 
			self.connection(start, last)
		else
 
			#  When invalid nodes
			print("\nHere Something Wrong\n")
		end

	end

	def printGraph() 
		if (self.size > 0) 
			index = 0
			#  Print graph ajlist Node value
			while (index < self.size) 
				print("\nAdjacency list of vertex ", index ," :")
				edge = self.node[index].next
				while (edge != nil) 
					#  Display graph node 
					print("  ", self.node[edge.id].data)
					#  Visit to next edge
					edge = edge.next
				end

				index += 1
			end

		end

	end

	#  Find indegree of each nodes of a given graph
	#  Find the incoming edges of each node
	def findIndegree(indegree) 
		if (self.size <= 0) 
			return
		end

		edge = nil
		i = 0
		while (i < self.size) 
			edge = self.node[i].next
			while (edge != nil) 
				#  Increase indegree of node
				indegree[edge.id] += 1
				#  Visit to next edge
				edge = edge.next
			end

			i += 1
		end

	end

	#  Find a sequence of topological sort
	def topologicalSort() 
		if (self.size <= 0) 
			return
		end

		status = false
		#   use to track node
		visit = Array.new(self.size) {false}
		#  Store indegree of node edges
		indegree = Array.new(self.size) {0}
		#  Find indegree of each node in graph
		self.findIndegree(indegree)
		print("\n")
		i = 0
		#  Find a node which indegree is 0
		while (i < self.size && status == false) 
			if (indegree[i] == 0) 
				status = true
			end

			i += 1
		end

		if (status) 
			#  When node exist which indegree zero
			print("\nResult : ")
			edges = nil
			i = 0
			#  Print a sequence of topological sort 
			#  in directed acyclic graph
			while (i < self.size) 
				if (indegree[i] == 0 && visit[i] == false) 
					#  Change to visit
					visit[i] = true
					print("  ", i)
					#  Get node edge
					edges = self.node[i].next
					while (edges != nil) 
						#  Reduce indegree
						indegree[edges.id] -= 1
						#  Visit to next node
						edges = edges.next
					end

					#  Reset loop execution
					i = -1
				end

				i += 1
			end

		else
 
			print("No topological Sort in this graph\n")
		end

	end

end

class GpaCalculator



	def initialize

	end


	def does_user_say_no question

		question == "stop"

	end
	def get_user_grade_and_add_all

		user_input = ""
		g = Graph.new(6)

		until does_user_say_no user_input
			
			user_input = gets.chomp
			grade_processor = GradeProcessor.new
			task = grade_processor.return_first_part user_input	
			if (!task.nil?)	
				if (!task[1].nil?)
				g.addEdge(Integer(task[0]), Integer(task[1]))
				else
				g.addEdge(Integer(task[0]))
				end 
			end
		 # @data.tsort

		end
			#  Print graph element
			g.printGraph()
			g.topologicalSort()


	end


	def calculate_gpa

		@gpa =  get_user_grade_and_add_all 
		@gpa

	end
	


	public :does_user_say_no

end